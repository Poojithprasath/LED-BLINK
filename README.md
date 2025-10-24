# LED-TOGGLE

## AIM:
Write an assembly language program in 8051 to generate a 5 ms delay using Timer 1 in Mode 1 and toggle an LED connected to Port 1.7 continuously

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software

 ## PROGRAM:
 ```
ORG 0000H
MOV TMOD, #10H
HERE:
MOV TH1, #0ECH
MOV TL1, #78H
SETB TR1
WAIT:
JNB TF1, WAIT
CLR TR1
CLR TF1
CPL P1.7
SJMP HERE
END
```
### OUTPUT:
![WhatsApp Image 2025-10-24 at 20 54 32_730c13a1](https://github.com/user-attachments/assets/ca93dd07-b367-4b0c-91bb-8f830047980b)

