<h1>Rextro Robot Car</h1>

<p><strong>Android app for controlling your robot car</strong></p>

<p>This app allows you to control the robot car using your phone’s built-in gyroscope. It also includes a joystick control option.</p>

<p><em>Tilt Control:</em></p>
<img width="976" height="986" alt="Tilt Control Interface" src="https://github.com/user-attachments/assets/f6b013d8-c03b-49fd-9f61-8239f0aadcd7" />

<p><em>Joystick Control:</em></p>
<img width="964" height="838" alt="Joystick Control Interface" src="https://github.com/user-attachments/assets/c6a61a64-3dea-4df7-bcd3-b844762ffd10" />

<p><em>Additionally, there are two addressable NeoPixel LEDs underneath the car. Using this interface, you can change the color of these LEDs.</em></p>

<img width="974" height="815" alt="LED Control Interface" src="https://github.com/user-attachments/assets/3a3295d3-8de5-422d-9b8b-a8ea3147b5c4" />

<h3>Emergency Stop Button</h3>

<p>Use this button to temporarily cut off transmission in case of an emergency:</p>

<p>
  <img width="176" height="150" alt="Stop Button" src="https://github.com/user-attachments/assets/6691a2c3-3c03-4274-928b-0f10075a98ad" />
  <img width="189" height="154" alt="Stop Icon" src="https://github.com/user-attachments/assets/3e663ba3-6779-400a-bbd1-495c3e86fb00" />
</p>

<p>The app supports full-duplex data transmission via BLE.</p>

<p>It also includes haptic feedback. Use this button to turn haptics ON or OFF:</p>

<img width="80" height="78" alt="Haptic Button" src="https://github.com/user-attachments/assets/3137d610-f2c5-4ce2-863e-e3446e1375b6" />

<hr>

<h2>Install Requirements</h2>
<ol>
  <li>Node.js + npm</li>
  <li>Cordova CLI — install with <code>npm install -g cordova</code></li>
  <li>Java JDK (set <code>JAVA_HOME</code>)</li>
  <li>Android Studio or Android SDK (Platform, Build-Tools, Platform-Tools). Make sure <code>ANDROID_SDK_ROOT</code> / <code>ANDROID_HOME</code> are set.</li>
</ol>

<h2>Create Project</h2>
<pre><code>cordova create rextro com.rextro.robot "Rextro Robot Car"
cd rextro
</code></pre>

<h2>Add your web app</h2>
<p>Replace everything inside the <code>www/</code> folder with your site:</p>
<pre><code>
www/
 ├── index.html
 ├── css/
 ├── js/
 └── assets/
</code></pre>

<h2>Add Android platform</h2>
<pre><code>cordova platform add android</code></pre>

<h2>Build APK</h2>
<ul>
  <li>Debug (quick test): <code>cordova build android --debug</code></li>
  <li>Release (unsigned): <code>cordova build android --release</code></li>
</ul>

<p><strong>APK output folder:</strong><br>
<code>platforms/android/app/build/outputs/apk</code></p>

<hr>

<h2>Modifying the App Interface</h2>
<p>The app interface is built with <strong>HTML, CSS, and JavaScript</strong> inside the `www` folder. To customize:</p>

<h3>HTML Layout (<code>index.html</code>)</h3>
<p>Add or remove buttons, sliders, or panels.</p>
<pre><code>&lt;button id="myButton"&gt;Click Me&lt;/button&gt;</code></pre>

<h3>CSS Styling (<code>css/style.css</code>)</h3>
<p>Change colors, fonts, sizes, or layout.</p>
<pre><code>#myButton {
    background-color: #ff0000;
    font-size: 18px;
}</code></pre>

<h3>JavaScript Behavior (<code>js/app.js</code>)</h3>
<p>Update event listeners for new buttons or controls.</p>
<pre><code>document.getElementById("myButton").addEventListener("click", function() {
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
<hr>

<h2>Rextro Robot Car Hardware & Firmware</h2>

<h3>Hardware Requirements</h3>
<table>
<thead>
<tr>
<th>Component</th>
<th>Model / Type</th>
</tr>
</thead>
<tbody>
<tr>
<td>Microcontroller</td>
<td>ESP32 Dev Board</td>
</tr>
<tr>
<td>Motors</td>
<td>DC Motors (2)</td>
</tr>
<tr>
<td>Motor Driver</td>
<td>L298N / H-Bridge equivalent</td>
</tr>
<tr>
<td>Ultrasonic Sensor</td>
<td>HC-SR04 (single pin mode)</td>
</tr>
<tr>
<td>Temperature Sensor</td>
<td>DHT11</td>
</tr>
<tr>
<td>RGB LED</td>
<td>WS2812 / NeoPixel (2 LEDs)</td>
</tr>
<tr>
<td>OLED Display</td>
<td>128x64 SSD1306</td>
</tr>
<tr>
<td>Headlights</td>
<td>2 x LEDs or small lamps</td>
</tr>
<tr>
<td>Power Source</td>
<td>7.4V Li-ion / 5V regulated</td>
</tr>
</tbody>
</table>

<h3>Wiring & Pin Configuration</h3>
<p>Ensure common ground between the ESP32 and the Motor Driver.</p>



[Image of ESP32 L298N motor driver wiring diagram]


<table>
<thead>
<tr>
<th>Function</th>
<th>Pin ESP32</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr>
<td>Left Motor A</td>
<td>16</td>
<td>PWM Output</td>
</tr>
<tr>
<td>Left Motor B</td>
<td>17</td>
<td>PWM Output</td>
</tr>
<tr>
<td>Right Motor A</td>
<td>18</td>
<td>PWM Output</td>
</tr>
<tr>
<td>Right Motor B</td>
<td>27</td>
<td>PWM Output</td>
</tr>
<tr>
<td>RGB LEDs</td>
<td>14</td>
<td>NeoPixel (GRB)</td>
</tr>
<tr>
<td>DHT11 Sensor</td>
<td>26</td>
<td>Data Pin</td>
</tr>
<tr>
<td>Ultrasonic</td>
<td>5</td>
<td>Trigger/Echo</td>
</tr>
<tr>
<td>Headlight 1</td>
<td>15</td>
<td>Digital Out</td>
</tr>
<tr>
<td>Headlight 2</td>
<td>2</td>
<td>Digital Out</td>
</tr>
<tr>
<td>OLED SDA</td>
<td>21</td>
<td>I2C</td>
</tr>
<tr>
<td>OLED SCL</td>
<td>22</td>
<td>I2C</td>
</tr>
</tbody>
</table>

<hr>

<h3>BLE Communication Protocol</h3>
<ul>
<li><strong>Device Name:</strong> <code>Rextro Robot Car</code></li>
<li><strong>Service UUID:</strong> <code>4fafc201-1fb5-459e-8fcc-c5c9c331914b</code></li>
<li><strong>Characteristic UUID:</strong> <code>beb5483e-36e1-4688-b7f5-ea07361b26a8</code></li>
</ul>

<h4>Command Packet (7 Bytes)</h4>
<table>
<thead>
<tr>
<th>Byte</th>
<th>Function</th>
<th>Range/Type</th>
</tr>
</thead>
<tbody>
<tr>
<td>0</td>
<td>Start Byte</td>
<td>0xFF</td>
</tr>
<tr>
<td>1</td>
<td>Forward/Back</td>
<td>-100 to 100</td>
</tr>
<tr>
<td>2</td>
<td>Turn</td>
<td>-100 to 100</td>
</tr>
<tr>
<td>3</td>
<td>Red</td>
<td>0-255</td>
</tr>
<tr>
<td>4</td>
<td>Green</td>
<td>0-255</td>
</tr>
<tr>
<td>5</td>
<td>Blue</td>
<td>0-255</td>
</tr>
<tr>
<td>6</td>
<td>Headlight</td>
<td>0=OFF, 1=ON</td>
</tr>
</tbody>
</table>

<hr>

<h3>OLED Display Status</h3>
<pre>
CONNECTED
FWD: 45    ██████████
TURN: -20  ████
RGB: 255 128 0
</pre>

<ol>
<li>Install <strong>Arduino IDE</strong> or <strong>PlatformIO</strong>.</li>
<li>Install Libraries: <code>Adafruit_SSD1306</code>, <code>Adafruit_GFX</code>, <code>Adafruit_NeoPixel</code>, <code>DHT sensor</code>, <code>ESP32 BLE Arduino</code>.</li>
<li>Ensure PWM pins are attached using <code>ledcAttachPin()</code>.</li>
<li>Compile and upload to ESP32.</li>
</ol>

<h3>Troubleshooting</h3>
<ul>
<li><strong>Motors not moving:</strong> Check PWM pins and wiring.</li>
<li><strong>BLE not connecting:</strong> Verify UUIDs match the App.</li>
<li><strong>OLED blank:</strong> Check I2C address (0x3C).</li>
</ul>

<hr>

<h1>Rextro Robot Car Customization</h1>

<p>Rextro Robot Car allows you to personalize your robot with a <strong>custom boot logo</strong> and a <strong>custom Bluetooth name</strong>.</p>

<hr>

<h2>1. Custom Boot Logo</h2>

<p>You can display any monochrome image on the OLED during startup.</p>

<h3>Step 1: Prepare Your Image</h3>
<ul>
  <li>Choose a <strong>black-and-white</strong> image (monochrome only).</li>
  <li>Recommended dimensions: <strong>128x64 pixels</strong>.</li>
  <li>Keep designs simple for clarity.</li>
</ul>

<h3>Step 2: Convert Image to Bitmap</h3>
<p>Use <a href="https://javl.github.io/image2cpp/" target="_blank">Image2CPP</a> to generate a C++ array:</p>
<ol>
  <li>Upload your image.</li>
  <li>Select <strong>Monochrome</strong> mode.</li>
  <li>Set <strong>Width = 128, Height = 64</strong>.</li>
  <li>Choose <strong>Vertical byte orientation</strong>.</li>
  <li>Copy the generated output as <code>const unsigned char logo[] PROGMEM</code>.</li>
</ol>

<h3>Step 3: Replace Logo in Code</h3>
<p>Locate the existing logo array in <code>Rextro_Robot_Car.ino</code>:</p>
<pre><code>const unsigned char epd_bitmap_Logo [] PROGMEM = { 
    0x00, 0x00, 0x00, ...
};</code></pre>

<p>Replace it with your new bitmap:</p>
<pre><code>const unsigned char epd_bitmap_Logo [] PROGMEM = {
    0xFF, 0xFF, 0x00, 0x00, ... // your bitmap values
};</code></pre>

<h3>Step 4: Adjust Display Code (Optional)</h3>
<pre><code>oled.drawBitmap(0, 0, epd_bitmap_Logo, 128, 64, WHITE);</code></pre>

<p>For smaller logos, you can center them:</p>
<pre><code>int logoWidth = 64;
int logoHeight = 32;
oled.drawBitmap((128-logoWidth)/2, (64-logoHeight)/2, epd_bitmap_Logo, logoWidth, logoHeight, WHITE);</code></pre>

<h3>Step 5: Compile and Upload</h3>
<ul>
  <li>Save changes, compile, and upload to the ESP32.</li>
  <li>Reset the board to see your custom boot logo on startup.</li>
</ul>

<hr>

<h2>2. Custom Bluetooth Name</h2>

<p>You can change the name the ESP32 broadcasts over BLE to make your robot easily recognizable.</p>

<h3>Step 1: Locate BLE Initialization</h3>
<pre><code>#define BLE_NAME "Rextro Robot Car"

BLEDevice::init(BLE_NAME);
BLEServer *pServer = BLEDevice::createServer();
BLEService *pService = pServer->createService(SERVICE_UUID);</code></pre>

<h3>Step 2: Change the Name</h3>
<p>Replace <code>"Rextro Robot Car"</code> with your preferred name:</p>
<pre><code>#define BLE_NAME "MyCustomBot"</code></pre>

<p>Keep it readable and under ~20 characters.</p>

<h3>Step 3: Recompile and Upload</h3>
<ul>
  <li>Save changes, compile, and upload the firmware.</li>
  <li>After reset, the ESP32 will advertise using the new Bluetooth name.</li>
</ul>

<blockquote>
  <strong>💡 Tip:</strong> Mobile devices may cache the old name; toggle Bluetooth off and on if the new name does not appear immediately.
</blockquote>

<hr>

<h1>REXTRO Animation Loop</h1>

<p>An interactive, animated loader for the <strong>REXTRO Robot App</strong>. Includes:</p>
<ul>
    <li>SVG logo stroke & fill animation</li>
    <li>Spinner rotation</li>
    <li>Dynamic star particle effects</li>
</ul>

<p>This guide explains how to adjust animation timings for a custom look.</p>

<h2>1. Logo Animation</h2>
<p>The logo stroke and fill animation is controlled via:</p>
<pre><code>.logo-anim {
    animation: fullCycle 8s ease-in-out infinite;
}</code></pre>

<h3>Keyframes Breakdown (Time Percentages)</h3>
<pre><code>@keyframes fullCycle {
    0%   { stroke-dashoffset: 4000; fill-opacity: 0; stroke: #fff; }        /* Start */
    60%  { stroke-dashoffset: 0; fill-opacity: 0; stroke: #fff; }           /* Stroke drawn */
    60%  { stroke-dashoffset: 0; fill-opacity: 1; stroke: transparent; }  /* Fill appears */
    80%  { stroke-dashoffset: 0; fill-opacity: 0; stroke: #fff; }           /* Fade out */
    100% { stroke-dashoffset: 4000; fill-opacity: 0; stroke: #fff; }      /* Reset */
}</code></pre>

<h3>Adjusting Timing</h3>
<p><code>8s</code> → full loop duration (adjust to speed up or slow down)</p>
<p>Keyframe percentages → control animation phases:</p>
<ul>
    <li>0–60% → stroke drawing</li>
    <li>60–80% → fill display</li>
    <li>80–100% → fade & reset</li>
</ul>

<h4>Example Adjustments</h4>
<table>
    <tr>
        <th>Phase</th>
        <th>Original</th>
        <th>Faster</th>
        <th>Slower</th>
    </tr>
    <tr>
        <td>Stroke Draw</td>
        <td>0–60%</td>
        <td>0–40%</td>
        <td>0–80%</td>
    </tr>
    <tr>
        <td>Fill Display</td>
        <td>60–80%</td>
        <td>40–60%</td>
        <td>80–90%</td>
    </tr>
    <tr>
        <td>Fade & Reset</td>
        <td>80–100%</td>
        <td>60–100%</td>
        <td>90–100%</td>
    </tr>
</table>

<blockquote>💡 Tip: Adjust percentages for precise control without changing the total duration.</blockquote>

<h2>2. Spinner Animation</h2>
<pre><code>.spinner {
    animation: spin 2s linear infinite;
}</code></pre>
<p>Duration = full rotation time. Reduce → faster spin, increase → slower spin.</p>
<p>Synchronize with logo by adjusting proportionally (e.g., logo = 8s, spinner = 2s).</p>

<h2>3. Star Particle Animation</h2>
<p>Stars have two animations: <strong>twinkle</strong> and <strong>drift</strong>.</p>
<pre><code>star.style.setProperty('--duration', (Math.random() * 4 + 2) + 's');        // Twinkle
star.style.setProperty('--move-duration', (Math.random() * 15 + 15) + 's'); // Drift
star.style.setProperty('--delay', (Math.random() * 5) + 's');               // Start offset</code></pre>

<ul>
    <li><code>--duration</code> → time for one twinkle cycle (2–6s)</li>
    <li><code>--move-duration</code> → time for one drift (15–30s)</li>
    <li><code>--delay</code> → start offset for variety (0–5s)</li>
</ul>

<h4>Star Timeline Example</h4>
<table>
    <tr>
        <th>Star Effect</th>
        <th>Start</th>
        <th>Midpoint</th>
        <th>End</th>
    </tr>
    <tr>
        <td>Twinkle</td>
        <td>opacity 0.2</td>
        <td>1</td>
        <td>0.2</td>
    </tr>
    <tr>
        <td>Drift</td>
        <td>position start</td>
        <td>halfway move</td>
        <td>end position</td>
    </tr>
</table>

<h2>4. Quick Summary Table</h2>
<table>
    <tr>
        <th>Animation</th>
        <th>Property / Variable</th>
        <th>Default</th>
        <th>Purpose</th>
    </tr>
    <tr>
        <td>Logo</td>
        <td>.logo-anim animation</td>
        <td>8s</td>
        <td>Full cycle speed</td>
    </tr>
    <tr>
        <td>Logo keyframes</td>
        <td>0–60%, 60–80%, 80–100%</td>
        <td>—</td>
        <td>Control phases</td>
    </tr>
    <tr>
        <td>Spinner</td>
        <td>.spinner animation</td>
        <td>2s</td>
        <td>Rotation speed</td>
    </tr>
    <tr>
        <td>Star Twinkle</td>
        <td>--duration</td>
        <td>2–6s</td>
        <td>Speed of twinkle</td>
    </tr>
    <tr>
        <td>Star Drift</td>
        <td>--move-duration</td>
        <td>15–30s</td>
        <td>Speed of drift</td>
    </tr>
    <tr>
        <td>Star Delay</td>
        <td>--delay</td>
        <td>0–5s</td>
        <td>Start offset for variety</td>
    </tr>
</table>

<h2>5. Tips for Developers</h2>
<ul>
    <li>Time percentages allow precise control of each animation phase.</li>
    <li>Synchronization: Adjust spinner & stars relative to logo animation.</li>
    <li>Visual Testing: Use GIFs or live browser preview to fine-tune timing.</li>
</ul>

<hr>

<h1>Rextro Robot Car Cordova Guide</h1>
<p>This guide explains how to configure your Cordova project so your <strong>custom HTML boot animation</strong> displays correctly on Android and how to change the overlay from white to black.</p>

<h2>1. Create a Cordova Project</h2>
<pre><code>npm install -g cordova
cordova create rextro com.rextro.robot "Rextro Robot Car"
cd rextro</code></pre>

<h2>2. Add Android Platform</h2>
<pre><code>cordova platform add android</code></pre>

<h2>3. Configure <code>config.xml</code></h2>
<p>Replace or edit your <code>config.xml</code> with the following settings:</p>
<pre><code>&lt;widget xmlns="http://www.w3.org/ns/widgets"
        xmlns:cdv="http://cordova.apache.org/ns/1.0"
        id="com.rextro.robot"
        version="1.0.0"&gt;
    &lt;name&gt;Rextro Robot Car&lt;/name&gt;
    &lt;description&gt;Rextro Robot Car App with custom boot animation&lt;/description&gt;
    &lt;author email="dev@cordova.apache.org" href="https://cordova.apache.org"&gt;Apache Cordova Team&lt;/author&gt;

    &lt;content src="index.html" /&gt;

    &lt;allow-intent href="http://*/*" /&gt;
    &lt;allow-intent href="https://*/*" /&gt;

    &lt;platform name="android"&gt;
        &lt;preference name="AndroidWindowSplashScreenBackground" value="#000000" /&gt;
        &lt;preference name="SplashScreenBackgroundColor" value="#000000" /&gt;
        &lt;preference name="SplashScreenDelay" value="0" /&gt;
        &lt;preference name="FadeSplashScreen" value="false" /&gt;
        &lt;preference name="ShowSplashScreen" value="true" /&gt;
    &lt;/platform&gt;
&lt;/widget&gt;</code></pre>

<h2>4. Key Preferences Explanation</h2>
<table>
    <tr><th>Preference</th><th>Purpose</th></tr>
    <tr><td>AndroidWindowSplashScreenBackground</td><td>Changes the boot overlay color. Set to black (#000000) to prevent white flash on Android 12+.</td></tr>
    <tr><td>SplashScreenBackgroundColor</td><td>Sets the splash screen background. Match with black for smooth animation transition.</td></tr>
    <tr><td>SplashScreenDelay</td><td>Duration splash screen is visible. Use 0 for instant HTML boot animation.</td></tr>
    <tr><td>FadeSplashScreen</td><td>Enable/disable fade effect. False ensures immediate animation.</td></tr>
    <tr><td>ShowSplashScreen</td><td>Must be true to show splash at app start.</td></tr>
</table>

<blockquote>
    <strong>Tip:</strong> Android 12+ shows a default white overlay before your splash screen. Set <code>AndroidWindowSplashScreenBackground="#000000"</code> to fix this.
</blockquote>

<h2>5. Add Your Boot Animation</h2>
<p>Place your custom animation HTML in the <code>www/</code> folder:</p>
<pre><code>www/
├─ index.html
├─ css/
│  └─ style.css
└─ js/
   └─ animation.js</code></pre>

<h2>6. Build and Run</h2>
<pre><code>cordova build android
cordova run android</code></pre>

<h2>7. Optional: Adjust Splash Timing</h2>
<table>
    <tr><th>Use Case</th><th>Value</th></tr>
    <tr><td>Instant boot (HTML handles timing)</td><td>0</td></tr>
    <tr><td>Give Cordova splash time</td><td>2000 (2 seconds)</td></tr>
</table>

<h2>Summary</h2>
<ul>
    <li>Edit <code>config.xml</code> to set black background for Android boot overlay.</li>
    <li>Ensure <code>index.html</code> contains your SVG animation and loader.</li>
    <li>Set <code>SplashScreenDelay=0</code> and <code>FadeSplashScreen=false</code> for smooth startup.</li>
    <li>Build and test on an Android device to see your animation immediately on boot.</li>
</ul>
