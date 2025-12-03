<b>Rextro Robot Car</b>

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

<b>*Install Requirements*</b>
<ol>
<li>Node.js + npm<br></li>
<li>Cordova CLI<br></li>
<li>npm install -g cordova<br></li>
<li>Java JDK<br></li>
<li>Android Studio or Android SDK (Platform, Build-Tools, Platform-Tools)<br></li>
</ol>

<b>*Create Project*</b>
````bash
cordova create rextro com.rextro.robot "Rextro Robot Car"
cd rextro
````
<b>*Add Your Web App*</b>

Replace everything inside the www/ folder with your own:

www/
 ├── index.html
 ├── css/
 ├── js/
 └── assets/

Add Android Platform
`cordova platform add android`

*Build APK*
Debug (quick test)
`cordova build android --debug`

<b>*Release (unsigned)*</b>
cordova build android --release


<b>*APK output folder:</b>*

`platforms/android/app/build/outputs/apk`




