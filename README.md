<h1 style="font-weight:900; color:#333;">Rextro Robot Car</h1>

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

<hr>
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
<hr>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DPBot Pro #2 Documentation</title>
    <style>
        /* GitHub-like Styling */
        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif;
            line-height: 1.6;
            color: #24292e;
            max-width: 900px;
            margin: 0 auto;
            padding: 20px;
        }
        h1, h2, h3 {
            border-bottom: 1px solid #eaecef;
            padding-bottom: 0.3em;
            margin-top: 24px;
        }
        table {
            border-collapse: collapse;
            width: 100%;
            margin: 16px 0;
        }
        th, td {
            border: 1px solid #dfe2e5;
            padding: 6px 13px;
        }
        th {
            background-color: #f6f8fa;
            font-weight: 600;
        }
        tr:nth-child(2n) {
            background-color: #f6f8fa;
        }
        code {
            background-color: #f6f8fa;
            border-radius: 3px;
            font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, Courier, monospace;
            padding: 0.2em 0.4em;
            font-size: 85%;
        }
        pre {
            background-color: #f6f8fa;
            padding: 16px;
            border-radius: 6px;
            overflow: auto;
            line-height: 1.45;
        }
        pre code {
            background-color: transparent;
            padding: 0;
            font-size: 100%;
        }
        blockquote {
            border-left: 0.25em solid #dfe2e5;
            color: #6a737d;
            padding: 0 1em;
            margin: 0;
        }
        hr {
            height: 0.25em;
            padding: 0;
            margin: 24px 0;
            background-color: #e1e4e8;
            border: 0;
        }
    </style>
</head>
<body>

    <h1>DPBot Pro #2</h1>
    <p><strong>Hardware & Firmware Documentation for ESP32 Robot Control</strong></p>

    <h2>Hardware Requirements</h2>
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

    <h2>Wiring & Pin Configuration</h2>
    <p>Below is the pin mapping for the ESP32. Ensure common ground between the ESP32 and the Motor Driver.</p>

    

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
                <td>NeoPixel, GRB, NEO_KHZ800</td>
            </tr>
            <tr>
                <td>DHT11 Temp Sensor</td>
                <td>26</td>
                <td>Data Pin</td>
            </tr>
            <tr>
                <td>Ultrasonic Sensor</td>
                <td>5</td>
                <td>Single-pin trigger/echo</td>
            </tr>
            <tr>
                <td>Headlight 1</td>
                <td>15</td>
                <td>Digital output</td>
            </tr>
            <tr>
                <td>Headlight 2</td>
                <td>2</td>
                <td>Digital output</td>
            </tr>
            <tr>
                <td>OLED SDA</td>
                <td>21</td>
                <td>Wire / I2C</td>
            </tr>
            <tr>
                <td>OLED SCL</td>
                <td>22</td>
                <td>Wire / I2C</td>
            </tr>
        </tbody>
    </table>

    <hr>

    <h2>BLE Communication Protocol</h2>
    <ul>
        <li><strong>BLE Device Name:</strong> <code>DPBot Pro #2</code></li>
        <li><strong>Service UUID:</strong> <code>4fafc201-1fb5-459e-8fcc-c5c9c331914b</code></li>
        <li><strong>Characteristic UUID:</strong> <code>beb5483e-36e1-4688-b7f5-ea07361b26a8</code></li>
    </ul>

    <h3>Command Packet (7 Bytes)</h3>
    <p>Sent from App to Robot.</p>
    <table>
        <thead>
            <tr>
                <th>Byte</th>
                <th>Function</th>
                <th>Type</th>
                <th>Description</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>0</td>
                <td>Start Byte</td>
                <td>0xFF</td>
                <td>Identifies valid packet</td>
            </tr>
            <tr>
                <td>1</td>
                <td>Forward/Backward</td>
                <td>int8_t</td>
                <td>Range: -100 to 100</td>
            </tr>
            <tr>
                <td>2</td>
                <td>Turn Value</td>
                <td>int8_t</td>
                <td>Range: -100 to 100</td>
            </tr>
            <tr>
                <td>3</td>
                <td>RGB Red</td>
                <td>uint8_t</td>
                <td>0-255</td>
            </tr>
            <tr>
                <td>4</td>
                <td>RGB Green</td>
                <td>uint8_t</td>
                <td>0-255</td>
            </tr>
            <tr>
                <td>5</td>
                <td>RGB Blue</td>
                <td>uint8_t</td>
                <td>0-255</td>
            </tr>
            <tr>
                <td>6</td>
                <td>Headlight ON/OFF</td>
                <td>uint8_t</td>
                <td>0 = OFF, 1 = ON</td>
            </tr>
        </tbody>
    </table>

    <h3>Sensor Notification (2 Bytes)</h3>
    <p>Sent from Robot to App (Notify).</p>
    <table>
        <thead>
            <tr>
                <th>Byte</th>
                <th>Function</th>
                <th>Type</th>
                <th>Notes</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>0</td>
                <td>Distance (cm)</td>
                <td>uint8_t</td>
                <td>Constrained 0–255</td>
            </tr>
            <tr>
                <td>1</td>
                <td>Temperature °C</td>
                <td>uint8_t</td>
                <td>Constrained 0–255</td>
            </tr>
        </tbody>
    </table>

    <hr>

    <h2>OLED Display & RGB Status</h2>
    <p><strong>Startup sequence:</strong> OLED init bar → BLE init bar → Robot logo (1 sec).</p>
    <p><strong>Live Status Display:</strong></p>
    <pre>
CONNECTED
FWD: 45    ██████████
TURN: -20  ████
RGB: 255 128 0
</pre>
    <p><em>RGB LEDs are controlled by BLE values and updated in real-time.</em></p>

    <hr>

    <h2>Software Setup</h2>
    <ol>
        <li>Install <strong>Arduino IDE</strong> or <strong>PlatformIO</strong>.</li>
        <li>Install the following libraries:
            <ul>
                <li><code>Adafruit_SSD1306</code></li>
                <li><code>Adafruit_GFX</code></li>
                <li><code>Adafruit_NeoPixel</code></li>
                <li><code>DHT sensor library</code></li>
                <li><code>BLE (ESP32 BLE Arduino)</code></li>
            </ul>
        </li>
        <li>Connect ESP32 and select correct board/port.</li>
        <li>Copy firmware code to the Arduino IDE or PlatformIO.</li>
        <li>Compile and upload.</li>
    </ol>
    <blockquote>
        <strong>Important:</strong> Make sure PWM pins are attached correctly using <code>ledcAttachPin()</code> as configured in the code.
    </blockquote>

    <h2>Usage Example</h2>
    <ol>
        <li>Power the robot via Li-ion or regulated supply.</li>
        <li>Pair with smartphone app (BLE) named <code>DPBot Pro #2</code>.</li>
        <li>Send 7-byte commands over BLE to control motors, RGB, and headlights.</li>
        <li>Observe OLED for live status bars.</li>
        <li>Receive real-time sensor notifications via BLE.</li>
    </ol>

    <h3>Example BLE Command Code</h3>
    <pre><code>uint8_t command[7] = {0xFF, 50, -20, 255, 128, 0, 1};
pCharacteristic->setValue(command, 7);
pCharacteristic->notify();</code></pre>

    <h2>Troubleshooting</h2>
    <ul>
        <li><strong>Motors not moving:</strong> check PWM pins, inversion flags (<code>invertLeft</code> / <code>invertRight</code>).</li>
        <li><strong>OLED not displaying:</strong> verify I2C connections and OLED address (<code>0x3C</code>).</li>
        <li><strong>BLE not connecting:</strong> ensure device name matches and BLE is advertising.</li>
        <li><strong>RGB LEDs not lighting:</strong> check NeoPixel wiring and <code>pixels.show()</code> updates.</li>
    </ul>

</body>
</html>




