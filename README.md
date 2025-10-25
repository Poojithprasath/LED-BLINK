# LED-TOGGLE

## AIM:
To Write an assembly language program in 8051 to generate a 5 ms delay using Timer 1 in Mode 1 and toggle an LED connected to Port 1.7 continuously

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software

## ALGORITHM:

1. **Start the program.**

2. **Initialize Timer 1 in 16-bit mode (Mode 1):**  
   - Load the `TMOD` register with `10H` to select Timer 1, 16-bit mode.  

3. **Begin the main loop (`HERE`):**  
   - Load `TH1` with `0ECH`.  
   - Load `TL1` with `78H`.  
   - These values define the initial timer count for the desired delay.

4. **Start Timer 1:**  
   - Set the `TR1` bit to begin counting.

5. **Wait for Timer 1 overflow:**  
   - Continuously monitor `TF1` (Timer 1 overflow flag).  
   - Stay in the loop (`WAIT`) until `TF1 = 1`, indicating the timer has overflowed.

6. **Handle overflow:**  
   - Clear `TR1` to stop the timer.  
   - Clear `TF1` to reset the overflow flag for the next cycle.

7. **Toggle the output pin P1.7:**  
   - Complement the bit P1.7.  
   - This inverts the pin state, generating a square wave on P1.7.

8. **Repeat the process:**  
   - Jump back to the label `HERE` to reload the timer and continue toggling.

9. **End program.**


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

### MANUAL CALCULATION:

 * Clock freq = 11.0592 MHz → 1 machine cycle ≈ 1.085 µs =5000 × 1.085 µs ≈ 5.425 ms
 * Delay=5425μs=5.425ms

### RESULT:
 Thus, the 8051 Assembly Language Program to blink an LED with a 50 ms delay using Timer1 in Mode1
 was successfully written  and simulated using Keil µVision.

