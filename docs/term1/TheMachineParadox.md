

# The Machine Paradox

!!! info
    
    **==FACULTY==**: Santiago Fuentemilla Garriga, Oscar Gonzalez, Josep Marti, Petra Garajová 

    **==CALENDAR==**: 16-10 → 28-10

    **==TRACK==** Instrumentation

<div style="clear:both;"></div>

!!! info "**Team**"
    
    Albert Vila Bonfill, Anna Fedele, Dhrishya Ramadass, Mihnea Nicolae Patrascu, Nicolo Baldi, Qianyin Du


## **Forensic Report: 3D Printer**


| Reporting Agency       | MDEF                           |
|----------------------------------------|--------------------------------|
| Case identifier                        | Forensics of the Obsolescence  |
| Identity of the submitter              | Albert Vila Bonfill, Anna Fedele, Dhrishya Ramadass, Mihnea Nicolae Patrascu, Nicolo Baldi, Qianyin Du                 |
| Date of receipt                        | 17/10/2023                     |
| Date of report                         | 28/10/2023               |
 

### **Examination** 
<div class="sketchfab-embed-wrapper">
    <iframe 
        title="3D Printer" 
        width= "100%"
        height="400px"
        frameborder="0" 
        ui-theme="dark"
        preload="0"
        allowfullscreen 
        mozallowfullscreen="true" 
        webkitallowfullscreen="true" 
        allow="autoplay; fullscreen; xr-spatial-tracking" 
        xr-spatial-tracking 
        execution-while-out-of-viewport 
        execution-while-not-rendered 
        web-share 
        src="https://sketchfab.com/models/e502641d13b24bd5b1fdc4618c199533/embed?autostart=1&ui_theme=dark">
    </iframe>
</div>

- ==Serial number==: 01 150929 1189
- ==Brand==: FUNDACIOCIM
- ==Model==: BCN3D+
- ==Year==: 2015
- ==Weight==: 11,6 kg
- ==Colour==: BLACK/BLUE
- ==Made in==: SPAIN


### **Forensic Questions**

- ==WHAT DOES IT DO?== A 3D printer ==creates three-dimensional objects by layering material== based on a digital design. Using a computer-aided design (CAD) model as a blueprint, the printer adds material layer by layer to form a solid object. 

- ==HOW DOES IT WORK?== Depending on the technology used, the printer deposits material with each layer fusing to the one below. The material is solidified using various methods like heating, UV curing, or laser sintering, resulting in a three-dimensional object that matches the digital design.

- ==HOW IS IT BUILT?== The 3D printer is constructed using a combination of mechanical, electronic, and software components. ==Mechanically==, it features a frame that houses the moving parts, including the print head or extruder, and a build platform. These components are driven by motors, guided by linear rails or rods, ensuring precise movements on the X, Y, and Z axes. ==Electronically==, a main control board processes digital instructions from the slicing ==software==, directing the motors and regulating the temperature of the print head or curing source. 

- ==WHY IT FAILED, OR IT WASN'T USED ANYMORE?== The 3D printer ==still functions, but it's an older, unstable model== with low accuracy and print quality.


### **Steps Taken**

1. Cleaned the dust off the printer and brought it to the MDEF room.
2. Disassembled using our toolbox.
3. Separated into three main parts as follows:
    - ==PLATE==: Horizontal surface that also gets heated and can be moved in all directions and where the plastic is  printed on;
    - ==STRUCTURE==: The part that supports the entire printing machine;
    - ==EXTRUDER==: Contains the motors to print 3D filament;
4. Laid out all parts individually and documented.

### **Testing**

After the disassembly process, we meticulously ==examined each individual component==. Utilizing a precision lab power supply and a high-resolution multimeter, we conducted comprehensive tests to determine the optimal voltage required for each component's functionality.

### **Results**

- ==HOW MANY MOTORS DID YOU FIND INSIDE?== Five motors used to move the extruder in the three axis to permit printing in 3D space.
‍
- ==DOES IT CONTAIN A COMPUTER OR MICROCONTROLLER?== Yes, an Arduino board and a RAMPS.
‍
- ==DID YOU FIND ANY SENSORS?== Yes, temperature sensors.

### **Conclusions**

- ==WHAT DID YOU LEARN?==
    - How a 3D printer is assembled.
    - How a 3D printer works.
    - How to power up each component individually.
    - Fundamental electronics.
    - How a step motor works.
‍
- ==WHAT SURPRISED YOU?==
    - The number of components, screws and pieces the printer had.
    - The fact that we can make the extruder work with just few    components.
    - How easy and repareable it is.
    - How much the 3D technology has improved since 2015.

!!! abstract "References"
    - https://www.bcn3d.com/ca/arxius-open-source/
    - https://reprapbcn.wordpress.com/tag/3dprinter/
    - https://www.youtube.com/watch?v=MJ61LIdlyww

!!! note ""

## **LifeX**

While the initial week was dedicated to disassembling and testing individual components, week 2 presented us with a unique challenge: to innovate and ==craft a new machine using parts extracted from the printer==. An intriguing twist to this assignment was the directive to design it to be ==as non-functional as possible==. This encouraged us to let our creativity run wild and embrace a playful approach.
So embraced an audacious and captivating concept: the ==LifeX, a "life expectancy predictor"==.
With a simple push of a button, a pen draws a line on a paper below, supposedly predicting the age at which the user will pass away. It's a tongue-in-cheek nod to the dubious claims of some fortune tellers. 

In truth, an ==Arduino board is programmed to halt at a random number==, influenced by the moment the user activates it.
The motor maneuvers the pen across what we playfully dub your 'life bookmark'. This ticket, more than just a whimsical prediction, serves as a keepsake from this pseudo-paranormal encounter. Hold onto it and cherish the memory of this unique experience!

### **Process**

<iframe 
    width="100%" 
    height="400" 
    src="https://www.youtube.com/embed/vosQQlPurCI?si=WorDul6GVfAR135Y" 
    title="YouTube video player" 
    frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen>
</iframe>

??? example "**Code for LifeX**"

    ``` py

        //Servomotor library
        #include <Servo.h>

        // Define stepper motor connections and steps per revolution:
        #define dirPin 2
        #define stepPin 3
        #define stepsPerRevolution 200

        //LCD settings
        #include <Wire.h> 
        #include <LiquidCrystal_I2C.h>
        LiquidCrystal_I2C lcd(0x27, 16, 2);

        //PEN ServoMotor
        Servo penMotor;  //define the servomotor
        int potpin = A1;  //define servomotor pin
        int val;          //variable for servomotor

        const int buttonPin = 4;  // the number of the pushbutton pin
        int buttonState = 0;      // variable for reading the pushbutton status

        const int buttonPin1 = 5;
        int buttonState1 = 0;
        int home = 0;
        int prediction = 0;
        int start = 0;

        long ranValue;

        void penUp(){
        //PEN UP
        delay(1000);
        val = 0;
        val = map(val, 0, 1023, 0, 180);  
        penMotor.write(val);    
        }

        void penDown(){
            //PEN DOWN
            val = 90;
            penMotor.write(val);
        }

        void setup() {

        Serial.begin(9600);
        // Declare pins as output:
        pinMode(stepPin, OUTPUT);
        pinMode(dirPin, OUTPUT);
        pinMode(buttonPin, INPUT);
        penMotor.attach(potpin);
        randomSeed(analogRead(0));

        lcd.begin();
        lcd.backlight();
        }

        void initit() {

        if ((buttonState == HIGH) && (home == 0)) {
            digitalWrite(dirPin, HIGH); 
            Serial.println("Reset...");    
            
            void penUp();
            prediction = 0;                      

            //Spin the stepper motor 5 revolutions fast:
            for (int i = 0; i < stepsPerRevolution; i++) {
            // These four lines result in 1 step:
            digitalWrite(stepPin, HIGH);
            delayMicroseconds(500);
            digitalWrite(stepPin, LOW);
            delayMicroseconds(500);
            }
        } else if (buttonState == LOW) {
            //Serial.println("Ready!");
            home = 1;
        }
        }

        void loop() {

        // read the state of the pushbutton value:
        buttonState = digitalRead(buttonPin);
        buttonState1 = digitalRead(buttonPin1);

        initit();

        if ((buttonState1 == LOW) && (home == 1)) {
        
            ranValue = random(0,23);  // 1000*20200
            ranValue = ranValue * 100;

            lcd.clear();
            lcd.setCursor(2,0);
            Serial.println("Predicting...");
            lcd.print("Predicting...");

            if (prediction == 0) {
            digitalWrite(dirPin, LOW);
            void penDown();
        
            for (int i = 0; i < ranValue; i++) {
                // These four lines result in 1 step:
                digitalWrite(stepPin, HIGH);
                delayMicroseconds(500);
                digitalWrite(stepPin, LOW);
                delayMicroseconds(500);
                prediction = 1;
            }
            //the prediction is done!
            lcd.clear();
            Serial.print("Your Lifex is: ");
            Serial.println(ranValue/23);
            lcd.setCursor(1,0);
            lcd.print("Your Lifex is: ");
            lcd.setCursor(7,1);
            lcd.print((ranValue/23)+10);
            
            //get back Home
            void penUp();
            delay(5000);
            home = 0;
            //initit();     
            } 
        }
        }
    ```

### **Final Result**

<div class="sketchfab-embed-wrapper"> 
    <iframe title="LIFEX MODEL" 
    width= "100%"
    height="400px"
    frameborder="0" 
    allowfullscreen mozallowfullscreen="true" 
    webkitallowfullscreen="true" 
    preload="0"
    allow="autoplay; fullscreen; xr-spatial-tracking" 
    xr-spatial-tracking 
    execution-while-out-of-viewport 
    execution-while-not-rendered 
    web-share 
    src="https://sketchfab.com/models/08612964146242d88ae1c344fdd2f36b/embed?autostart=1&ui_theme=dark">
     </iframe> 
</div>

### **Presentation**

<iframe 
    style="border: 0px solid rgba(0, 0, 0, 0.1);" 
    width="100%" 
    height="450" 
    src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Fproto%2FcLFrMEDN6GybFAvQkN2E2G%2FLifeX-Presentation%3Fpage-id%3D21%253A2%26type%3Ddesign%26node-id%3D22-31%26viewport%3D584%252C397%252C0.15%26t%3De066V1nWbNjhBLNr-1%26scaling%3Dcontain%26mode%3Ddesign" 
    allowfullscreen></iframe>

### **Video**

<iframe 
    title="vimeo-player" 
    src="https://player.vimeo.com/video/878611346?h=13229e04f0" 
    width="100%" 
    height="385" 
    frameborder="0"    
    allowfullscreen></iframe>

!!! note ""