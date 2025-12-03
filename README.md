<b><h1>Rextro Robot Car</h1></b>

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
<strong>Install Requirements</strong>
<ol>
  <li>Node.js + npm</li>
  <li>Cordova CLI — install with <code>npm install -g cordova</code></li>
  <li>Java JDK (set <code>JAVA_HOME</code>)</li>
  <li>Android Studio or Android SDK (Platform, Build-Tools, Platform-Tools). Make sure <code>ANDROID_SDK_ROOT</code> / <code>ANDROID_HOME</code> are set.</li>
</ol>

<strong>Create Project</strong>
<pre><code class="bash">cordova create rextro com.rextro.robot "Rextro Robot Car"
cd rextro
</code></pre>

<strong>Add your web app</strong>
<p>Replace everything inside the <code>www/</code> folder with your site:</p>
<pre><code>
www/
 ├── index.html
 ├── css/
 ├── js/
 └── assets/
</code></pre>

<strong>Add Android platform</strong>
<pre><code class="bash">cordova platform add android</code></pre>

<strong>Build APK</strong>
<ul>
  <li>Debug (quick test): <code>cordova build android --debug</code></li>
  <li>Release (unsigned): <code>cordova build android --release</code></li>
</ul>

<p><strong>APK output folder:</strong><br>
<code>platforms/android/app/build/outputs/apk</code></p>


<strong><h2>Modifying the App Interface</strong></h2>
<p>The app interface is built with <strong>HTML, CSS, and JavaScript</strong> inside the <code>www</code> folder. To customize:</p>

<h3>HTML Layout (<code>index.html</code>)</h3>
<p>Add or remove buttons, sliders, or panels.</p>
<pre lang="html"><code>&lt;button id="myButton"&gt;Click Me&lt;/button&gt;</code></pre>

<h3>CSS Styling (<code>css/style.css</code>)</h3>
<p>Change colors, fonts, sizes, or layout.</p>
<pre lang="css"><code>#myButton {
    background-color: #ff0000;
    font-size: 18px;
}</code></pre>

<h3>JavaScript Behavior (<code>js/app.js</code>)</h3>
<p>Update event listeners for new buttons or controls.</p>
<pre lang="javascript"><code>document.getElementById("myButton").addEventListener("click", function() {
    alert("Button clicked!");
});</code></pre>

<h3>Testing Changes</h3>
<ul>
    <li>Use a browser for quick UI tests.</li>
    <li>Use <code>cordova run android</code> / <code>cordova run ios</code> to test on device.</li>
</ul>

<h3>Optional: Add New Screens</h3>
<ul>
    <li>Create new HTML pages and link via buttons.</li>
    <li>Update <code>app.js</code> to handle new interactions and BLE commands.</li>
</ul>





