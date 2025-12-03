Rextro Robot Car

Android app for controlling your robot car

This app allows you to control the robot car using your phone’s built-in gyroscope. It also includes a joystick control option.

*Tilt Control:*
<img width="976" height="986" alt="image" src="https://github.com/user-attachments/assets/f6b013d8-c03b-49fd-9f61-8239f0aadcd7" />
*Joystick Control:*
<img width="964" height="838" alt="image" src="https://github.com/user-attachments/assets/c6a61a64-3dea-4df7-bcd3-b844762ffd10" />

*Additionally, there are two addressable NeoPixel LEDs underneath the car. Using this interface, you can change the color of these LEDs.*

<img width="974" height="815" alt="image" src="https://github.com/user-attachments/assets/3a3295d3-8de5-422d-9b8b-a8ea3147b5c4" />

*Emergency Stop Button*

Use this button to temporarily cut off transmission in case of an emergency:

<img width="176" height="150" alt="image" src="https://github.com/user-attachments/assets/6691a2c3-3c03-4274-928b-0f10075a98ad" /> <img width="189" height="154" alt="image" src="https://github.com/user-attachments/assets/3e663ba3-6779-400a-bbd1-495c3e86fb00" />

The app supports full-duplex data transmission via BLE.

It also includes haptic feedback.
Use this button to turn haptics ON or OFF:

<img width="80" height="78" alt="image" src="https://github.com/user-attachments/assets/3137d610-f2c5-4ce2-863e-e3446e1375b6" />

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Use Apache Cordava to convert index.html into apk.
step by step guild:-
https://cordova.apache.org/docs/en/latest/guide/cli/installation.html

*Install Requirements*

1)Node.js + npm
2)Cordova CLI
3)npm install -g cordova
4)Java JDK
5)Android Studio or Android SDK (Platform, Build-Tools, Platform-Tools)

*Create Project*
'''bash
cordova create rextro com.rextro.robot "Rextro Robot Car"
cd rextro

📂 Add Your Web App

Replace everything inside the www/ folder with your own:

www/
 ├── index.html
 ├── css/
 ├── js/
 └── assets/

📱 Add Android Platform
cordova platform add android

🛠️ Build APK
Debug (quick test)
cordova build android --debug

Release (unsigned)
cordova build android --release


APK output folder:

platforms/android/app/build/outputs/apk/

🔌 Install on Device
adb install -r app-debug.apk

🔐 Sign Release APK
keytool -genkey -v -keystore my-release-key.jks -alias rextro_alias
zipalign -v -p 4 app-release-unsigned.apk app-release-aligned.apk
apksigner sign --ks my-release-key.jks --out app-release-signed.apk app-release-aligned.apk


Final APK:

app-release-signed.apk



Here is a clean, professional, and formatted README.md file based on your instructions. You can copy and paste this directly into your GitHub repository.

🤖 Rextro Robot Car
Rextro Robot Car is an Apache Cordova-based mobile application designed to interface with and control the Rextro Robot. This project wraps standard web technologies (HTML, CSS, JS) into a native Android APK.

📋 Prerequisites
Before building this project, ensure you have the following installed on your development machine:

Node.js + npm: Download Node.js

Java JDK: Ensure JAVA_HOME is set correctly.

Android Studio (or Command Line Tools):

Android SDK Platform

Android SDK Build-Tools

Android SDK Platform-Tools

Cordova CLI:

Bash

npm install -g cordova
🚀 Getting Started
1. Project Initialization
If you are starting from scratch or re-initializing the project:

Bash

# Create the project
cordova create rextro com.rextro.robot "Rextro Robot Car"

# Navigate into the directory
cd rextro
2. Application Source (www/)
The core logic of the application resides in the www/ folder. Replace the default Cordova files with your web application code.

Directory Structure:

Plaintext

rextro/
├── www/
│   ├── assets/      # Images, icons, fonts
│   ├── css/         # Stylesheets
│   ├── js/          # JavaScript logic
│   └── index.html   # Entry point
├── config.xml
└── ...
3. Add Android Platform
Initialize the Android platform environment:

Bash

cordova platform add android
🛠️ Building the APK
Debug Build (Testing)
Use this for quick testing during development. The APK will be signed with a debug key.

Bash

cordova build android --debug
Release Build (Production)
Use this to generate an unsigned release APK ready for signing.

Bash

cordova build android --release
📂 Output Location: Both builds will output the APK to: platforms/android/app/build/outputs/apk/

🔌 Install on Device
To install the Debug version directly to a connected Android device (ensure USB Debugging is enabled on the phone):

Bash

adb install -r platforms/android/app/build/outputs/apk/debug/app-debug.apk
🔐 Signing the Release APK
To prepare the app for the Play Store or public distribution, you must sign the release APK.

1. Generate Keystore
Skip this if you already have a keystore (.jks file).

Bash

keytool -genkey -v -keystore my-release-key.jks -alias rextro_alias
2. Align the APK
Optimize the APK layout (Zipalign):

Bash

zipalign -v -p 4 app-release-unsigned.apk app-release-aligned.apk
3. Sign the APK
Sign the aligned APK using your keystore:

Bash

apksigner sign --ks my-release-key.jks --out app-release-signed.apk app-release-aligned.apk
✅ Final Output
Your distributable file is: app-release-signed.apk

Would you like me to...


