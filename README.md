# LED-TOGGLE

## AIM:
To Write an assembly language program in 8051 to generate a 5 ms delay using Timer 1 in Mode 1 and toggle an LED connected to Port 1.7 continuously

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software

## ALGORITHM:
1.Start the program.
2.Initialize the timer mode:
 Load the TMOD register with the value 10H.
 This sets Timer 1 in Mode 1 (16-bit timer mode).
3.Start the main loop (HERE):
  Load the TH1 register with 0ECH.
  Load the TL1 register with 78H.
   → Together, these values define the initial timer count.
4.Start Timer 1:
  Set the TR1 bit (Timer Run Control for Timer 1) to start the timer.
5.Wait for overflow:
  Continuously check the TF1 flag (Timer 1 overflow flag).
  Stay in this loop (WAIT) until TF1 = 1 (overflow occurs).
6.After timer overflow:
  Clear the TR1 bit → Stop Timer 1.
  Clear the TF1 flag → Reset overflow flag for next use.
7.Toggle the output pin:
  Complement (invert) the bit P1.7.
  → If it was 0, it becomes 1; if it was 1, it becomes 0.
  → This produces a square wave on pin P1.7.
8.Repeat continuously:
  Jump back to label HERE to reload timer and repeat the process.
9.End the program.

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

### RESULT:
 Thus, the 8051 Assembly Language Program to blink an LED with a 50 ms delay using Timer1 in Mode1
 was successfully written  and simulated using Keil µVision.

