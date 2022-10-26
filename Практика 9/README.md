# Отчет №9
## Сергей Голубкин 
### Группа 8310


[Ссылка на проект.](https://www.tinkercad.com/things/1oMi9YHurDI-copy-of-keyboard-and-screen/editel?sharecode=kqr27YDZdhaier1OzuhVxAYRqHh62sp1zRT57h2_uow)

![Изображение](https://user-images.githubusercontent.com/115896672/198039158-0213fbb2-bc35-470f-91a2-7b1247ecf2f2.png)







//////1
```С++
#include<Keypad.h> 
#include<LiquidCrystal.h>
int pressing,right=0;
String password_stp_total="24685";
String password_stp_option;
LiquidCrystal lcd(7, 6, 5, 4, 3, 2);
const byte ROWS = 4; 
const byte COLS = 4;
char hexaKeys[ROWS][COLS] = {
{'1','4','7'},
{'2','5','8'},
{'3','6','9'},
};
byte rowPins[ROWS] = {10,9,8};
byte colPins[COLS] = {13,12,11}; 
Keypad customKeypad = Keypad( makeKeymap(hexaKeys), rowPins, colPins, ROWS, COLS); 
void setup(){
lcd.begin(16, 2);
Serial.begin(9600);
}
void loop(){
  if (password_stp_option!="24685")
  {
    lcd.begin(16, 2);
    lcd.print("enter password");

    while(1)
    {
      char customKey = customKeypad.getKey(); 
      if (customKey)
      {
          pressing++;
          lcd.clear();
          password_stp_option+=customKey;
          lcd.print(password_stp_option);
          if (customKey==password_stp_total[right])
          {
              right++;
          }
          else
          {
              right=0; 
          }
          if (pressing==5)
          {
              if (right==5)
              {
                lcd.clear();
                lcd.print("welcome");
                delay(1000);
                right=0;
                pressing=0;
                password_stp_option="246985";
                lcd.clear();
                break;
              }
              if (right<5)
              {
                lcd.clear();
                lcd.print("password accepted");
                delay(1000);
                right=0;
                pressing=0;
                password_stp_option="";
                lcd.clear();
                break;
              }
          }
      }
  	}
  }  
  else
  {
    char customKey = customKeypad.getKey(); 
      if (customKey)
      {
        Serial.println(customKey);
        lcd.setCursor(0,0);
        lcd.print(customKey);
      if (customKey=='2'||customKey=='4'||customKey=='6'||customKey=='8')
        {
            lcd.setCursor(0,1);
            lcd.print("even");
        }
      else
        {
            lcd.setCursor(0,1);
            lcd.print("odd ");
        }
      }
  }
}

```

## Блок-схема
![Диограмма]()



## Пояснение





