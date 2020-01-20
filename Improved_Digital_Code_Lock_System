//The system basically allows one to unlock the system based on the safety key the user enters.
//LEDs are indicators of sucessful unlocking or failure
//There are limits set in the system for keeping the same password . One can keep the same password max of 5 times
//If the user enters wrong password for 3 times consecutively then he/she is entitled to have a long wait after which they are again allowed to enter the password again
//This is basically to ensure more protection
//Improvement is based on the fact that this ensures more protection than systems wherein you keep a same standard password and never change it and this is also more safe as if wrong password threshold is reached he/she who tries to enter the system basically cant unlock it for a long time(predefined) because the system identifies them as people trying to hack the system illegally 
#include <Keypad.h>

const byte numRows= 4; //number of rows on the keypad
const byte numCols= 4; //number of columns on the keypad

//keymap defines the key pressed according to the row and columns just as appears on the keypad
char keymap[numRows][numCols]= 
{
{'1', '2', '3', 'A'}, 
{'4', '5', '6', 'B'}, 
{'7', '8', '9', 'C'},
{'*', '0', '#', 'D'}
};

//Code that shows the the keypad connections to the arduino terminals
byte rowPins[numRows] ={7,6,5,4}; //Rows 0 to 3
byte colPins[numCols]= {3,2,1,0}; //Columns 0 to 3
char pass[4];
char pass1[4];
int flage;
int flagp;
//initializes an instance of the Keypad class
Keypad myKeypad= Keypad(makeKeymap(keymap), rowPins, colPins, numRows, numCols);
int ij=0;
int j=0;
int j1=0;
void setup()
{
  pass1[0]='1';
  pass1[1]='2';
  pass1[2]='2';
  pass1[3]='1';
  flage=0;
  flagp=0;
Serial.begin(9600);
  while (! Serial); // Wait untilSerial is ready
  Serial.println("Welcome to Digital Code Lock System.\nEnter the 4 digit digital code for unlocking your door\n");
pinMode(9, OUTPUT);
pinMode(10, OUTPUT);
pinMode(11, OUTPUT);
pinMode(13, OUTPUT);
}
int fj=0;
int flag1=0;
void loop()
{
  while(j<4)
{
char key=myKeypad.getKey();
if(key)
{
pass[j]=key;
Serial.print(pass[j]);
j++;
}
}
Serial.print("\n");
if(j==4)
{
  ij=0;
  while(ij<4)
  {
    if(pass[ij]!=pass1[ij])
    {
      flag1+=1;
      //Serial.print(flag1);
    }
    
    ij++;
  }
}
//Serial.print(flag1);
if((j==4)&&(flag1==0))
{
  Serial.println("You have successfully unlocked your system\n");
  flage=0;
  flagp+=1;
  j=0;
   digitalWrite(10, HIGH);   // turn the LED on (HIGH is the voltage level)
   delay(4000);              // wait for a second
   digitalWrite(10,LOW);    // turn the LED off by making the voltage LOW
   fj=1;
}
else if((j==4)&&(flag1>0))
{
  Serial.println("Your attempt to unlock your system was unsuccessful.Try Again!!!");
  flage+=1;
  j=0;
   digitalWrite(11, HIGH);   // turn the LED on (HIGH is the voltage level)
   delay(4000);              // wait for a second
   digitalWrite(11,LOW);    // turn the LED off by making the voltage LOW
   fj=1;
}
j=0;
flag1=0;
if(flage==3)
{
  flage=0;
  digitalWrite(13, HIGH);
  Serial.println("As you have exceeded the limit of unsuccessfully unlocking three times your system at a strech try again after buzzer stops\n");
  delay(30000);
  digitalWrite(13,LOW); 
  Serial.println("Now you can retry your attempt");
}
if(flagp==5)
{
  flagp=0;
  flage=0;
  Serial.println("The maximum limit for keeping the same password is 5 successful attempts.\nTo continue change your 4 digit password\n");
     while(j1<4)
{
char keyk=myKeypad.getKey();
if(keyk)
{
pass1[j1]=keyk;
Serial.print(pass1[j1]);
j1++;
}
}
Serial.println("Password Changed Successfully\n"); 
   digitalWrite(9, HIGH);   // turn the LED on (HIGH is the voltage level)
   delay(4000);              // wait for a second
   digitalWrite(9,LOW);    // turn the LED off by making the voltage LOW
j1=0;
}
if(fj==1)
{
  fj=0;
  Serial.println("Enter the 4 digit digital code for unlocking your door\n");
}
}
