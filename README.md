#define m11 11   //left rear motor
#define m12 12  
#define m9 9    //right rear motor
#define m8 8
char str[2];
int i = 0;
void forward()
{
  digitalWrite(m11,HIGH);
  digitalWrite(m12,LOW);
  digitalWrite(m9,HIGH);
  digitalWrite(m8,LOW);
}
void backward()
{
  digitalWrite(m11,LOW);
  digitalWrite(m12,HIGH);
  digitalWrite(m9,LOW);
  digitalWrite(m8,HIGH);
}
void left()
{
  digitalWrite(m11,LOW);
  digitalWrite(m12,LOW);
  digitalWrite(m9,HIGH);
  digitalWrite(m8,LOW);
}
void right()
{
  digitalWrite(m11,HIGH);
  digitalWrite(m12,LOW);
  digitalWrite(m9,LOW);
  digitalWrite(m8,LOW);
}
void Stop()
{
  digitalWrite(m11,LOW);
  digitalWrite(m12,LOW);
  digitalWrite(m9,LOW);
  digitalWrite(m8,LOW);
}

void setup()
{
Serial.begin(9600);  // start serial communicatiion
pinMode(m12,OUTPUT);      //make m12 as output
pinMode(m11,OUTPUT);     //make m11 as output
pinMode(m9,OUTPUT);     //make m9 as output
pinMode(m8,OUTPUT);     //make m8 as output
}

void loop() {
  while(Serial.available())        //enters the loop only if any letter pressed in serial monitor
  {
    char ch = Serial.read();           //read the value in typed in serial monitor and stores it in 'ch'
    str[i++] = ch;

    if(str[i-1] == '1')
    {
      forward();
      i = 0;
    }
    if(str[i-1] == '2')
    {
      right();
      i = 0;
    }
    if(str[i-1] == '3')
    {
      left();
      i = 0;
    }
    if(str[i-1] == '4')
    {
      backward();
      i = 0;
    }
    if(str[i-1] == '5')
    {
      Stop();
    }
    delay(100);
  }
}
