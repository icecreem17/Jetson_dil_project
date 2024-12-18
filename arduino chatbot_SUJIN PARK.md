# jetson_arduino_chatbot
This repository shows the results of creating a chatbot on Jetson Nano's Python to answer real-time concentrations.


### This is the code that you need to create a Python virtual environment on Jetson Nano, then open the Jupiter laptop, create a file, and enter it.

```
# Install the required package. Pysserial is a library for serial communication.
!pip install pyserial

# smbus is a package that supports I2C communication.
!pip install smbus

# Update and install the openai library to the latest version.
!pip install -U openai

# Gets the basic Python standard library and OpenAI API.
import os  # Managing Environmental Variables
from openai import OpenAI  # For OpenAI API calls
import json  # Modules for JSON Data Processing

# Store the OpenAI API key in an environment variable.
os.environ['OPENAI_API_KEY'] = ''  # API Key
OpenAI.api_key = os.getenv("OPENAI_API_KEY")  # Gets the API key from the environment variable.

# Get the Jetson GPIO (Library for GPIO control on the Jetson board).
import Jetson.GPIO as GPIO
import time  # Module for time control
import math  # a mathematical arithmetic module
import serial  # Serial Communication Library

def measure_co2():
    SERIAL_PORT = "/dev/ttyUSB0"  # Change to a real connected port
    BAUD_RATE = 9600

    try:
        with serial.Serial(SERIAL_PORT, BAUD_RATE, timeout=10) as ser:
            ser.write(b'\x11\x01\x01\xED')  # CM1106 Sensor Command
            time.sleep(10)  # Waiting time for response

            # 응답 데이터 읽기
            response = ser.read_all()  # Read all possible data
            print(f"Raw response (bytes): {response}")

            try:
                response = response.decode('ascii')  # Attempt to decode
                print(f"Decoded response: {response}")
            except Exception as decode_error:
                print(f"Decoding error: {decode_error}")
                return "Error: Failed to decode response."

            if response.startswith("CO2:"):
                co2_value = response.split(":")[1].strip()
                return co2_value
            else:
                print("response: " + response)
                print("Error: Unexpected response format.")
                return "Error: Unexpected response format."

    except serial.SerialException as e:
        print(f"Serial connection error: {e}")
        return "Error: Serial connection issue."

    except Exception as e:
        print(f"Error during measurement: {e}")
        return f"Error: {e}"

measure_co2()

# Function to measure CO2 concentration and determine if ventilation is required
def determine_ventilation_status(co2_value):
    try:
        co2_value = int(co2_value)  # Converting user-supplied CO2 values to integers
    except ValueError:
        return "Please enter a valid CO2 concentration e.g. 900 ppm"

    # Determination of ventilation according to CO2 concentration range
    if co2_value < 800:
        status = "Concentration is at the right level. No ventilation is required."
    elif co2_value <= 1000:
        status = "The concentration is a bit high. Ventilation is recommended."
    else:
        status = "The air quality is bad due to the high concentration. Immediate ventilation is required."

    # Return Final Message
    return f"The current CO2 concentration is {co2_value}ppm. {status}"

# Add to function list to determine CO2 status in interactions with OpenAI
use_functions = [
    {
        "type": "function",
        "function": {
            "name": "measure_co2",
            "description": "Reads CO2 concentration from a CM1106 sensor connected via serial port and returns the measured value in ppm."
        }
    },
    {
        "type": "function",
        "function": {
            "name": "determine_ventilation_status",  # Function name
            "description": "Determines ventilation needs based on CO2 concentration."
        }
    }
]

def ask_openai(llm_model, messages, user_message, functions = ''):
    client = OpenAI()
    proc_messages = messages

    if user_message != '':
        proc_messages.append({"role": "user", "content": user_message})

    if functions == '':
        response = client.chat.completions.create(model=llm_model, messages=proc_messages, temperature = 1.0)
    else:
        response = client.chat.completions.create(model=llm_model, messages=proc_messages, tools=functions, tool_choice="auto") 

    response_message = response.choices[0].message
    tool_calls = response_message.tool_calls

    if tool_calls:
        # Step 3: call the function
        # Note: the JSON response may not always be valid; be sure to handle errors

        available_functions = {
            "measure_co2": measure_co2,
            "determine_ventilation_status": determine_ventilation_status
        }

        messages.append(response_message)  # extend conversation with assistant's reply

        # Step 4: send the info for each function call and function response to GPT
        for tool_call in tool_calls:
            function_name = tool_call.function.name
            function_to_call = available_functions[function_name]
            function_args = json.loads(tool_call.function.arguments)


            
            print(function_args)
           

            if function_name == "measure_co2":
                co2_result= function_to_call(**function_args)
                
                ventilation_result = available_functions["determine_ventilation_status"](co2_result)

                proc_messages.append(
                    {
                        "tool_call_id": tool_call.id,
                        "role": "tool",
                        "name": "determine_ventilation_status",
                        "content": ventilation_result,
                    }
                )
                
            else:
                
                if 'user_prompt' in function_args:
                    function_response = function_to_call(function_args.get('user_prompt'))
                else:
                    function_response = function_to_call(**function_args)
    
    
                proc_messages.append(
                    {
                        "tool_call_id": tool_call.id,
                        "role": "tool",
                        "name": function_name,
                        "content": function_response,
                    }
                )  # extend conversation with function response

                
        second_response = client.chat.completions.create(
            model=llm_model,
            messages=messages,
        )  # get a new response from GPT where it can see the function response

        assistant_message = second_response.choices[0].message.content
    else:
        assistant_message = response_message.content

    text = assistant_message.replace('\n', ' ').replace(' .', '.').strip()


    proc_messages.append({"role": "assistant", "content": assistant_message})

    return proc_messages, text

import gradio as gr
import random


messages = []

def process(user_message, chat_history):

    # def ask_openai(llm_model, messages, user_message, functions = ''):
    proc_messages, ai_message = ask_openai("gpt-4o-mini", messages, user_message, functions= use_functions)

    chat_history.append((user_message, ai_message))
    return "", chat_history

with gr.Blocks() as demo:
    chatbot = gr.Chatbot(label="Chat")
    user_textbox = gr.Textbox(label="Input")
    user_textbox.submit(process, [user_textbox, chatbot], [user_textbox, chatbot])

demo.launch(share=True, debug=True)
```
