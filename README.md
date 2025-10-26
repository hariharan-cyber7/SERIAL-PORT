
# Serial Transfer of Single Byte / Character using 8051 (Keil)

## AIM
To write and execute an Embedded C Program for Serial Transfer of Single Byte / Character using 8051 in Keil.

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software  

## PROGRAM

### (i) Serial Port Transfer a Single Character

```
ORG 00H
MOV TMOD,#20H
MOV TH1, #0FDH
MOV SCON, #40H
SETB TR1
MOV SBUF, #'B'
WAIT: JNB TI,WAIT
CLR TI
END

```
### (ii) Serial Port to Transfer a Message

```
#include <reg51.h>
void main(void)
{
    unsigned char msg[] = "Hariharan B";
    unsigned char i;
    TMOD = 0x20;
    TH1  = 0xFA;
    SCON = 0x50;
    TR1  = 1;
    for(i = 0; msg[i] != '\0'; i++)
    {
        SBUF = msg[i];
        while(TI == 0);
        TI = 0;
    }

    while(1);
}
```

### OUTPUT:
###  (i) Serial Port Transfer a Single Character
<img width="1237" height="511" alt="image" src="https://github.com/user-attachments/assets/2863e045-bf51-4a11-bde1-adb2c0adc0db" />

###  (ii) Serial Port to Transfer a Message
<img width="1463" height="580" alt="image" src="https://github.com/user-attachments/assets/964ee1ba-d49c-4018-83cc-666d70a63520" />

### RESULT:
Thus the Serial transfer of Single Byte / Character using 8051 KEIL was done and shown the output.
