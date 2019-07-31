---
# About hats-ci
---
The hats-ci installer installs packages needed to run browsers automated functional test on Windows. Simplifies the steps to setup test environment in Windows.

We believe that agile quality practices accelerate the delivery of quality applications. To deal with a growing test backlog, test automation is a more scalable and cost-effective approach.

As a group of passionate quality engineers, we want to lower the barrier of entry to web app test automation so that everyone can contribute to software quality.

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
To write/edit a robot script, you can use the following IDEs
1. [Eclipse IDE](https://eclipse.org/)  with [RED plugin](https://github.com/nokia/RED). 
   - Open command prompt/terminal and type `red` in hats_shell to begin
2. [Visual Studio Code](https://code.visualstudio.com/)
   - Enable Robot Framework Intellisense Extension
3. [Pycharm IDE](https://www.jetbrains.com/pycharm/) with [IntelliBot plugin](https://plugins.jetbrains.com/plugin/7386-intellibot)
4. [Notepad++](https://notepad-plus-plus.org/)

---
## Android Automation using Appium
---

---
## Browser Automation using Robotcorder
---

Browsers
- Microsoft Internet Explorer 11
- Microsoft Edge 44 (or newer)
- Google Chrome 54 (or newer)
- Mozilla Firefox 54 (or newer)
- Apple Safari 10 and later

> Something here





# Run robot scripts using hats-ci 

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
