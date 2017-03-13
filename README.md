# WEEK8
WEEK 8 

int mySensVals[5] = {20,40,60,80,100};
int mySensVals_index=0;
// this constant won't change:
const int  buttonPin = 2;    // the pin that the pushbutton is attached to
//const int ledPin = ;       // the pin that the LED is attached to
const int servomotorPin = 13;   // the pin that the motor is attached to

// Variables will change:
int buttonPushCounter = 0;   // counter for the number of button presses
int buttonState = 0;         // current state of the button
int lastButtonState = 0;     // previous state of the button

void setup() {
  // put your setup code here, to run once:
  // initialize the button pin as a input:
  pinMode(buttonPin, INPUT);
  // initialize the motor as an output:
  pinMode(servomotorPin, OUTPUT);
  // initialize serial communication:
  Serial.begin(9600);

}

void loop() {
  // put your main code here, to run repeatedly:
  // read the pushbutton input pin:
  buttonState = digitalRead(buttonPin);
  
  // compare the buttonState to its previous state
  if (buttonState != lastButtonState) {
    // if the state has changed, increment the counter
     Serial.println("Enter  buttonState pressed");
    
     Serial.println( mySensVals[mySensVals_index]);
     mySensVals_index++;
      if(mySensVals_index>4)
     {  mySensVals_index=0;}
     
    if (buttonState == HIGH) {
      // if the current state is HIGH then the button
      // wend from off to on:
      buttonPushCounter++;
      Serial.println("on");
      Serial.print("number of button pushes:  ");
      Serial.println(buttonPushCounter);
    } else {
      // if the current state is LOW then the button
      // wend from on to off:
      Serial.println("off");
    }
    // Delay a little bit to avoid bouncing
   // delay(5);
  }
  // save the current state as the last state,
  //for next time through the loop
  lastButtonState = buttonState;
  

  // turns on the servomotor every four button pushes by
  // checking the modulo of the button push counter.
  // the modulo function gives you the remainder of
  // the division of two numbers:
  if (buttonPushCounter % 4 == 0) {
    
  
     
    digitalWrite(servomotorPin, HIGH);
  } else {
    digitalWrite(servomotorPin, LOW);
   }

  

}
