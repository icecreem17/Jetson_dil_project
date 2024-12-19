# Jetson_dli_SUJIN PARK

## Learn the basics of Jetson Nano
```
Supplies
1. Jetson Nano
2. monitor(Recommend having a monitor in addition to your computer. If you use it on your computer (especially a laptop), there is a possibility of an OS collision.)
3. LAN USB
4. power(You have to use 5A with power. If you use more than that, Jetson Nano will be ruined.)
5. Wired mouse and keyboard(Wireless mice and keyboards are also available, but this repository does not show how to connect them.)
6. SD card(least to 32 GB)
7. USB Camera(It doesn't matter if I use another camera, but this repository only covers USB-Camera.)

P. S. MY laptop OS is Window. If your computer's OS is not Windows, steps 2-3 are different. So please find a method that suits your computer.
      And since the steps in this file are difficult to do in one day, we recommend doing them 3-4 hours a day for 2-3 days.
```






## 1. Download images


![화면 캡처 2024-12-19 014545](https://github.com/user-attachments/assets/86d6c6e6-bd53-4e94-bd7e-ccc3e40dafa8)


### GO to 'https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write' and download the file for your computer's operating system.
### And unzip the image file.






## 2. Format your SD Card for SD Memory Card Formatter program


![화면 캡처 2024-12-19 015407](https://github.com/user-attachments/assets/de929b3f-c47d-4e2b-bacf-6bbf7a4a091f)
![image](https://github.com/user-attachments/assets/93e80f1f-637a-4640-bc16-8b1e15d5176b)
![image](https://github.com/user-attachments/assets/b4469e0d-5d19-46ec-9052-6c69eaf8435f)


### GO to 'https://sd-memory-card-formatter.en.softonic.com/download','https://etcher.balena.io/' and download the file' and download the file.
### When you finish download, format your sd card(follow image 2,3).






## 3. Bake downloaded images


![image](https://github.com/user-attachments/assets/1dcca447-5a4c-44cb-a1a7-ab75c26267c8)
![image](https://github.com/user-attachments/assets/e60f4365-91be-494b-be4d-cbb34a498998)
![image](https://github.com/user-attachments/assets/fb537deb-05e8-4fb1-a027-92270fd95fd0)
![image](https://github.com/user-attachments/assets/6a442712-7a56-411a-ae5a-70f32e7cb444)
![image](https://github.com/user-attachments/assets/8564ede9-f2bb-4505-bf6e-2900e18cb466)
![image](https://github.com/user-attachments/assets/32f7ba98-a506-481d-840f-ba73ebf9ac4b)


### GO to 'https://etcher.balena.io/','https://etcher.balena.io/' and download the file' and download the file.
### When you finish download, Put the image you downloaded in step 1 into your SD card.
### Then, follow the image 2-6 times, and bake the downloaded image.






## 4. Assemble Jetson Nano


![KakaoTalk_20241128_214356790_04](https://github.com/user-attachments/assets/1bc22d5f-6785-476f-ac9a-f135a0e2cbf7)


### - Insert the SD card containing the baked image into the Jetson Nano slot and gently press it. 
### - Insert the hdmi wire cable. 
### - Insert wired mouse and keyboard cables.
### - Insert wired LAN USB.
### - Connecting the power(5A).






## 5. Jetson Nano Installation


### Install Jetson Nano following the images below.


![KakaoTalk_20241128_214356790_06](https://github.com/user-attachments/assets/4b14d757-ca1a-4d19-bf7a-0f4fcaffb056)
![KakaoTalk_20241128_214356790_12](https://github.com/user-attachments/assets/b11d5f87-b292-4c07-9d8c-0d6a85fe0b8f)
![KakaoTalk_20241128_214356790_16](https://github.com/user-attachments/assets/5c4005e4-fa96-47de-9ac6-5ac0b3910a3b)
![KakaoTalk_20241128_214356790_17](https://github.com/user-attachments/assets/48ab2db5-89b9-417a-807a-5b7fc9f931b3)
![KakaoTalk_20241128_214356790_20](https://github.com/user-attachments/assets/cb21e048-b21a-482b-9f8d-634485670470)


### Choose English.(image 4,5 )


![KakaoTalk_20241128_214356790_22](https://github.com/user-attachments/assets/51633137-b97f-449c-8a09-5c6f78a6ec1e)
![KakaoTalk_20241128_214356790_26](https://github.com/user-attachments/assets/c929d2a8-beb0-4b5a-a261-baef39327d08)
![KakaoTalk_20241128_214356790_28](https://github.com/user-attachments/assets/47a1c001-c143-431b-b514-861efb227cd7)
![KakaoTalk_20241128_214356790_29](https://github.com/user-attachments/assets/aee9b4e0-6780-4ef0-acba-e928affd6af3)


### Choose the capital of your country.


![KakaoTalk_20241128_214356790_30](https://github.com/user-attachments/assets/9f88e68e-61e5-471d-929c-d351c24c8dcc)


### Make your name and password the same. And as in the example, it's easy to remember to make short.


![KakaoTalk_20241128_215122143_05](https://github.com/user-attachments/assets/c7fdf4c7-c706-465f-8e3a-eeeba64e7a6b)
![KakaoTalk_20241128_215122143_06](https://github.com/user-attachments/assets/af0d4989-abee-4526-bb51-b2532081b657)


### Add Maxium accepted size as it says in the computer window.


![image](https://github.com/user-attachments/assets/65f95c51-5c90-47ec-a8f6-16e8adffbb32)
![KakaoTalk_20241128_215122143_08](https://github.com/user-attachments/assets/b48c60c4-aa59-4f3c-8a87-5834e51799a5)
![KakaoTalk_20241128_215122143_12](https://github.com/user-attachments/assets/32e79e12-0922-4293-9217-bbe66d048d15)
![KakaoTalk_20241128_215122143_14](https://github.com/user-attachments/assets/49ade21d-a3af-4635-a03a-5a3f2c3843aa)
![image](https://github.com/user-attachments/assets/a92db102-bc7d-4f01-aa89-06383f92a2ad)

### Computer reboot is start.
![KakaoTalk_20241128_215122143_15](https://github.com/user-attachments/assets/6159f73f-805a-484f-b3b9-2388ee6ccbd0)
![KakaoTalk_20241128_215122143_17](https://github.com/user-attachments/assets/c95807d0-4bbe-4ec8-b5f5-a5c0cdcfc87b)
![KakaoTalk_20241128_215122143_18](https://github.com/user-attachments/assets/ae50df59-96ef-43fa-a0d9-86e638e95146)

### The Jetson Nano installation is complete.






## 6. Examine L4T-Readme & ifconfig


### You can skip these steps and Please refer to the blog that details how to use Jetson Nano.


![KakaoTalk_20241128_215122143_19](https://github.com/user-attachments/assets/3d77df6f-0ff0-4d9a-b201-8dc84d2dff2e)
![KakaoTalk_20241128_215122143_21](https://github.com/user-attachments/assets/3263f7eb-895d-4bb7-8be7-e3aba589c84a)
![KakaoTalk_20241128_215122143_22](https://github.com/user-attachments/assets/5828ac46-de94-413e-93e6-8cf08725c402)
![KakaoTalk_20241128_215122143_23](https://github.com/user-attachments/assets/3de86873-b4b9-4252-a88a-472b54de5b6e)
![KakaoTalk_20241128_215122143_24](https://github.com/user-attachments/assets/bdef3423-d426-4aaf-adb3-d9a915b7e8a9)
![KakaoTalk_20241128_215122143_25](https://github.com/user-attachments/assets/8c33fbe3-9deb-49a7-912b-323b1f0d9ccb)
![KakaoTalk_20241128_215122143_26](https://github.com/user-attachments/assets/bd2d09fa-d29c-421d-bee4-adaa42f379a3)


### You can enter the password you set.

![KakaoTalk_20241128_215122143_28](https://github.com/user-attachments/assets/9d038fcb-3435-4bb4-9bec-5b983047220b)


### This image is checking Jetson Nano Hardware Running.


```
code
sudo nmcli device wifi list
```


![KakaoTalk_20241128_215122143_29](https://github.com/user-attachments/assets/c8c6cc3a-d95d-4612-9213-36895f6110e6)


### This image is checking Jetson Nano ifconfig.


```
code
ifconfig
```






## 7. Installing languages that Jackson Nano does not include


### If your native language is English or you are fluent in it, skip thins process. but if you don't, install your native language.
### This course is the process of installing your native language (except English) and took Hangul as an example.


![KakaoTalk_20241128_215141595_02](https://github.com/user-attachments/assets/f7dce8e4-fcf5-4de0-af0f-b5ab9ec1159d)


```
code
sudo apt-get update
```


![KakaoTalk_20241128_215141595_04](https://github.com/user-attachments/assets/80d9d093-4d5f-4e84-b0ce-0a96d1f37363)
![KakaoTalk_20241128_215141595_07](https://github.com/user-attachments/assets/80d1186a-c0d1-4b41-82b5-4bd142c9383d)


### On the last line, [ Do you want to continue? [Y/n] ]'s written on the last line. So enter 'y'.


![KakaoTalk_20241128_215141595_08](https://github.com/user-attachments/assets/f158951f-d387-44e6-8731-4caf60857506)


```
code
sudo apt-get install fcitx-hangul
```


### fictx-hangul : Ask Chatgpt or another AI what file code is installing your native language.


![KakaoTalk_20241128_215141595_09](https://github.com/user-attachments/assets/9de4399b-457f-4f23-ab09-2e91577308e0)


### On the last line, [ Do you want to continue? [Y/n] ]'s written on the last line. So enter 'y'.


![image](https://github.com/user-attachments/assets/418c4afc-bac7-4634-85f9-3e58ef54125b)


### In Jetson Nano Setting, press the 'Region & Language' button and execute the Managed Language button.


![KakaoTalk_20241128_215141595_12](https://github.com/user-attachments/assets/c9bdb197-d3f2-4921-b06d-42ec0268fabf)


### If it runs as above, it says that it installs various language-related things. And install them.


![KakaoTalk_20241128_215141595_14](https://github.com/user-attachments/assets/18cf6daa-1836-4e0a-bddb-835961929f68)
![KakaoTalk_20241128_215141595_16](https://github.com/user-attachments/assets/0aec0515-3358-42de-a6d5-82ffba3369a8)
![KakaoTalk_20241128_215141595_17](https://github.com/user-attachments/assets/9787bb6d-34c8-42f6-8ffa-118f4538b00e)


### When the installation is complete, change the lower keyboard input method system item to fcitx.
### And reboot by entering the code below.


```
code
im-config -n fcitx
```


![KakaoTalk_20241114_184028807](https://github.com/user-attachments/assets/e7bd0456-608a-486b-8ed4-6df9e4007686)
![KakaoTalk_20241114_184028807_01](https://github.com/user-attachments/assets/6f5923d1-277b-4f20-a6fa-071122d3d931)


### When the Add input method window appears, uncheck "Only Show Current Language" and enter your native language to search for it.


![KakaoTalk_20241114_184028807_02](https://github.com/user-attachments/assets/53871aeb-74bb-432b-b43c-2ce575c0791e)


### Your native language addition is done, and it looks like above. Keyboard-English (US) can or can't be.


![KakaoTalk_20241114_184028807_03](https://github.com/user-attachments/assets/1e10cd75-019e-4310-aeea-fe65a15e5839)


### Now click the Global Config tab in the Input Method Configuration.


![KakaoTalk_20241114_184028807_04](https://github.com/user-attachments/assets/548d8c5e-c6bb-44b4-badc-056601b73fe8)


### Click the left button of the Trigger Input Method, and then press "your navte Youngkey" to replace it, and it's over.


![image](https://github.com/user-attachments/assets/71150216-59a8-402a-b1a1-8a1e6a41ba68)
![Screenshot from 2024-11-14 20-51-02](https://github.com/user-attachments/assets/46ddcb10-888a-4458-9901-f863b119ff4d)


### Press the keyboard on the top or bottom of the right or your keyboard Language Conversion keyt o get a Korean-style Taegeuk pattern.(or your nation pattern)
### If the shape of the national flag came out, it's completed.






## 8. Jackson Nano Photography & Video Capture


### From here on, the explanation process is for code, and the execution results are shown.
### If you want to know the explanation process, I recommend you to take the nvidia(dil) < Getting started with AL on Jetson Nano( explain in english ) > lecture.


```
code
sudo apt install python3-pip
```

### do you want to continue ? enter 'y'.


```
code
sudo -H pip3 install -U jetson-stats
````

### if you get an error, Enter the code below.


```
code
sudo apt-get upgrade
sudo apt-get update
````


### Verify that the version of jetson-stats-4.2.3 or higher has been written.


```
code
sudo apt-get reboot
sudo apt-get jtop
````


![image](https://github.com/user-attachments/assets/7b33ddca-c504-4b57-b9ee-8393d3c1eec5)


### Install a cooling fan because you can see that the temperature is very high.


```
code
sudo sh -c 'echo 128 > /sys/devices/pwm-fan/target_pwm
sudo apt-get jtop
````


### Check Jetson Nano's temperature.
### Connect the Jetson Nano and USB-Camera.


```
code
ls /dev/vi*
git clone https://github.com/jetsonhacks/USB-Camera.git
ls
cd USB-Camera
ls
python3 usb-camera-gst.py
````


### A camera-illuminated screen is shown on the Jetson Nano.


```
code
cd USB-Camera
ls
python3 face-detect-usb.py
````


### Face recognition is recognized by the camera.


```
code
nvgstcapture-1.0 --mode=1 --camsrc=0 --cap-dev-node=0 --automate --capture-auto
````


### Then, To capture the picture, Click the mouse and press 'j'.
### click the mouse and press 'q'. your image is captured and restored in file home.
### Examples(below)


![image](https://github.com/user-attachments/assets/4f6050d6-6fe3-41dd-886a-4f8b2a7a6888)
![Screenshot from 2024-11-14 20-59-17](https://github.com/user-attachments/assets/1ddb0609-342e-42b7-8a71-1262b339d05b)


```
code
nvgstcapture-1.0 --mode=2 --camsrc=0 --cap-dev-node=0
````


### Then, To capture the video, Click the mouse and press '1'(start).
### Second, Click the mouse and press 01'(stop).
### Last, click the mouse and press 'q'. your video is captured and restored in file home.
### Examples(below)


https://github.com/user-attachments/assets/753b3ac5-ee2d-4176-bb74-15c2a446380b






## 9. NviDiA images download


### From here on, the execution results are only shown(not explanation).
### If you want to know the explanation process, I recommend you to take the nvidia(dil) < Getting started with AL on Jetson Nano( explain in english ) > lecture.


![Screenshot from 2024-11-14 21-45-16](https://github.com/user-attachments/assets/950ff074-5eb5-486b-b481-387118ec2d9f)
![Screenshot from 2024-11-14 21-45-32](https://github.com/user-attachments/assets/60e8b810-42c9-4dd8-8294-44478b930d15)
![Screenshot from 2024-11-21 18-54-55](https://github.com/user-attachments/assets/9586b14b-d830-40a7-b480-eaff1186b8e7)


## 10. Create a swap 18 GB


![스왑 사진  jpg](https://github.com/user-attachments/assets/a7e28215-6e86-488c-8f4b-01feaf3d4039)
### -> Process of setting to GUI mode during reboot


![Screenshot from 2024-11-21 20-20-05](https://github.com/user-attachments/assets/9793be0a-ea05-4966-9041-73e2d057b8b4)
### -> Memory increased from 1.9 gigabytes to 18 gigabytes


## 3. Access to Jupiter Notebook


![Screenshot from 2024-11-21 19-33-56](https://github.com/user-attachments/assets/cc3f49f8-a8ee-41e4-9002-1b09daa73b44)


## 4. Learning Thumb Orientation Photography


![Screenshot from 2024-11-21 20-15-42](https://github.com/user-attachments/assets/a9084f30-7b82-4cbb-94a6-bd2273331c10)


## 5. Complete thumb direction photo prediction


![Screenshot from 2024-11-21 20-23-43](https://github.com/user-attachments/assets/e84f3a5c-9297-408d-9863-99cf1b86ab61)
![Screenshot from 2024-11-21 20-24-24](https://github.com/user-attachments/assets/39db115d-eaa8-46e2-bc2b-9e46daa147e7)
