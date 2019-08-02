---
# About hats-ci
---
The hats-ci installer installs packages needed to run browsers automated functional test on Windows. Simplifies the steps to setup test environment in Windows.

We believe that agile quality practices accelerate the delivery of quality applications. To deal with a growing test backlog, test automation is a more scalable and cost-effective approach.

As a group of passionate quality engineers, we want to lower the barrier of entry to web app test automation so that everyone can contribute to software quality.

**Tested on the following browsers**

| Browsers                                                    | Version  | Status  | 
| :---------------------------------------------------------: |:--------:|:------: |
| <img src="https://imgur.com/863k356.png" width="30">        |    54    |    ✓    | 
| <img src="https://imgur.com/TXdtHM6.png" width="30">        |    54    |    ✓    | 
| <img src="https://imgur.com/SoY4fY8.png" width="30">        |    44    |    ✓    | 
| <img src="https://imgur.com/ZNOsXLB.png" width="30">        |    10    |    ✓    | 
| <img src="https://imgur.com/CZvGPpG.png" width="30">        |    11    |    ✓    | 

**Main Features**

| Feature                 | Android | Browser | Date |  Status  |
| ----------------------- |:-------:|:------: |:----:|:---------:|
| Parallel Execution      |    ✓    |    ✓    | 2018 |Completed |
| Robot logs              |    ✓    |    ✓    | 2018 |Completed |
| Screen recordings       |    ✓    |    ⧖   | 2019  |In progress |
 

---
# Installation Guide
---
Operating Systems
- Windows 7, 8.1, 10 (64-bit)
- Mac OS X El-Capitan, macOS Sierra, High Sierra, Mojave
- Linux CentOS, Fedora, Ubuntu

Steps recommended for quickly getting started on automated testing based on your operating system

## Windows
1. Download the latest release (Link to release here)
2. Run hats_for_Windows_xx.exe
   - Administrator rights is required for first install
   - Changes will be made to your PATH variable and registry to allow hats to run
3. After installation, restart your computer
4. Open your command prompt/power shell and run `hats_shell` to load the virtual environment

## Mac OS
1. Ensure that you have Xcode installed before installing hats
2. Open your terminal and run the following command

`bash <(curl -s https://raw.githubusercontent.com/GovTechSG/hats-ci/master/assets/mac-installer.sh)`
3. Enter your login password when prompted
4. Installation will take about 20-30mins
5. After installation, re-open your terminal and ensure that `(hats)` virtual environment has loaded

## Linux 
For Ubuntu, run `bash <(curl -s https://raw.githubusercontent.com/younglim/hats-linux/master/assets/ubuntu-installer.sh)`

For CentOS/7 and Fedora, navigate to (link here) for more details


---
# Write Robot Scripts
---

**You will learn how to:**
* Generate android and browser commands using various tools
* Write robot scripts using robot framework

To write/edit a robot script, you can use the following IDEs
1. [Eclipse IDE](https://eclipse.org/)  with [RED plugin](https://github.com/nokia/RED). 
   - Open command prompt/terminal and type `red` in hats_shell to begin
2. [Visual Studio Code](https://code.visualstudio.com/)
   - Enable Robot Framework Intellisense Extension
3. [Pycharm IDE](https://www.jetbrains.com/pycharm/) with [IntelliBot plugin](https://plugins.jetbrains.com/plugin/7386-intellibot)
4. [Notepad++](https://notepad-plus-plus.org/)


## Android Automation using UiAutomator


## Android Automation using Appium Desktop

**Getting Started**
1. Download [Appium Desktop](https://github.com/appium/appium-desktop/releases/tag/v1.13.0)
2. Complete the Appium installation and launch Appium Desktop
3. Ensure that you are connect to your android device
4. (Check if need enable USB debugging mode)
5. Click on start server
6. Click on the search icon to start inspector session

   <img src="https://imgur.com/KkTTMv9.png" width="500">

7. Enter the [desired capabilities](https://github.com/appium/appium/blob/master/docs/en/writing-running-appium/caps.md) as shown below and click on start session

   <img src="https://imgur.com/8drFhQA.png" width="900">

8. When the session loads, a screenshot of your app will appear on the left. 

   <img src="https://imgur.com/xETX4tr.png" width="900">

9. Congrats! You have successfully connected to your android device using Appium desktop

**Interacting with the device**

Now, we will interact with various UI elements and use appium to turn these interactions into robot scripts

1. Mouse over various UI elements in your application, and see them highlighted.

   <img src="https://imgur.com/Wrm1UgV.png" width="900">

2. When an element is highlighted, its information will appear in the detailed view on the right side of the inspector.

   <img src="https://imgur.com/F85NIzp.png" width="500">

**Using the recorder**

1. Click on the recorder icon on appium desktop

   <img src="https://imgur.com/z6dSMv8.png" width="400">

2. When you start recording, the inspector will show an additional window
   
   <img src="https://imgur.com/tpvFCmD.png" width="700">

3. The recorder will show no code until some form of action (E.g. Tap on element) is taken 

   <img src="https://imgur.com/Zc4iPfb.png" width="400">

4. After tapping on the element, you should see the codes generated by appium recorder
   
   <img src="https://imgur.com/3RItUNl.png" width="500">




## Writing your first android robot script 
1. Open up your IDE (E.g. Visual Studio,Eclipse IDE)

2. Prepare the environment to run the robot script by copying the following codes to your IDE

   ```robotframework
   *** Settings ***
   Library          SeleniumLibrary
   Suite Teardown   Close Browser
   
   *** Variables ***
   ${APPIUM_PORT}   4723
   ${APPIUM_SERVER1}    http://localhost:${APPIUM_PORT}/wd/hub
   ${PLATFORM_VERSION}     8.0
   ${DEVICE_NAME}  Pixel_2_API_26
   ${DEVICE_UDID}  e12345678
   ${DRIVER_PATH}  null
   ```
3. Add in keywords to set up the android phone

   ```robotframework
   *** Keywords ***
   Setup and open android phone
       ${caps}=    create dictionary    platformName=Android    platformVersion=${PLATFORM_VERSION}     udid=${DEVICE_UDID}    deviceName=${DEVICE_NAME}    browserName=chrome  executable_path=${DRIVER_PATH}    create webdriver    Remote  command_executor=${APPIUM_SERVER1}    desired_capabilities=${caps}  
    ```

## Browser Automation using Robotcorder



> Something here

---
# Run robot scripts using hats-ci 
---

**You will learn how to:**
* Get started with Hats-ci
* Run robot scripts using Hats-ci
* View logs and recordings generated

## Step 0. Pre-requisites
* Ensure that you have already downloaded the latest version of [hats-ci](https://github.com/younglim/hats-ci)
* Downloaded [Scrcpy](https://github.com/Genymobile/scrcpy) - For screen mirroring and recording (Optional)
* Downloaded the web browsers (E.g. Google Chrome, Microsoft Edge) that you want to test on 
* Have a basic understanding of [robot framework](https://robotframework.org/robotframework/latest/RobotFrameworkUserGuide.html) 


## Step 1. Check out the folder structure

After downloading the latest version of hats-ci, you will see hats folder.

Navigate to the robot_automation folder as shown below to explore the folder structure

    hats
    ├── robot_automation        
    │   ├── browserlogs              # Logs for web browsers (E.g. Chrome, Firefox)
    │   ├── drivers                  # Chrome Drivers for Windows, Mac and Linux
    |   ├── hatslib.robot            # Main Robot Script
    |   ├── logs                     # Logs for mobile devices (E.g. Android)
    |   ├── src                      # Python Source files
    │   └── testscripts              # Sample Robot Test Scripts
    |       ├── web_test.robot       # For browser automation
    |       ├── resource.robot
    |       ├── android.robot        # For android google chrome
    |       └── android_app.robot    # For android mobile applications
    └── ...

## Step 2. Execute hats.lib

**Windows**
1. Load hats virtual environment on your command prompt by running `hats_shell`
2. Navigate to the robot_automation folder by running the following command on your command prompt
```
   cd C:\Program Files\hats\robot_automation
```

**Mac**
1. Open a terminal and ensure that `(hats)` virtual environment has loaded
2. Navigate to the robot_automation folder

**Execute hats.lib**
3. Run the main robot script to execute the other robot test scripts
   ```
   robot hatslib.robot
   ```
   The sample robot test scripts that can be executed by hatslib.robot are shown below
   
   <img src="https://imgur.com/mEFPTll.png" width="500">
   
4. Review our snippet of hatslib.robot (Main robot script)
   
   <img src="https://imgur.com/jV2GJQ1.png" width="600">
   
   *Note: Excluded Android_app.robot test script and focused on web and mobile automation of browsers
   

## Step 3. Android automation in session

1. Ensure that you are connected to at least one android device by running `adb devices`on your command prompt/terminal

2. If you are connected to this device for the first time using [adb](https://developer.android.com/studio/command-line/adb), allow usb debugging

   <img src="https://imgur.com/6xls19Q.png" width="200">

3. Once you run hatslib.robot (main robot script), the robot test scripts located within the test scripts folder are executed

4. It will run the first robot test script - android.robot

5. If Scrcpy is downloaded, Scrcpy will launch the display of the connected android device 

6. You should see the test being executed when the google chrome mobile application is launched


## Step 4. Browser automation in session

1. Once android.robot has completed running, it will move on to the second robot test script - web_test.robot

2. The test will be executed and multiple web browser will launch at the same time


## Step 5. Verify the results
1. Once the test has completed, you can view the logs and report located within browserlogs and logs folder for more details

   ![img](https://media.giphy.com/media/LSckueQa9fnd0hhm3G/giphy.gif)

2. If Scrcpy is downloaded, users of hats-ci will have screen recordings of the robot test scripts executing on android devices. These recordings are saved within the logs folder

   Sample mobile screen recordings shown below
   
   ![img](https://media.giphy.com/media/SqTvGesL8C228P0C95/giphy.gif)

   *Note: Screen recording is only available for automation of android devices and not browser automation

3. The logs for both android and browser automation have also been compressed and zipped according to the execution date and time




Continue from here??

Send keys

<img src="https://imgur.com/2Gra7WU.png" width="300">
