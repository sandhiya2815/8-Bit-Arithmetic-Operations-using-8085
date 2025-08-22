# 8-Bit-Arithmetic-Operations-using-8085
## Aim:
To perform 8-bit arithmetic operations such as addition, subtraction, multiplication, and division using the 8085 microprocessor.
Apparatus Required:
•	Laptop with internet connection
## Algorithm:
## For Addition (With Carry Consideration):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Add the contents of registers A and B.
4.	If carry is generated, store carry in 4301H.
5.	Store the sum in memory location 4300H.
## For Subtraction (Considering Greater Number):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Compare A and B.
4.	If A < B, swap the values of A and B to ensure positive result.
5.	Subtract the content of B from A.
6.	Store the result in memory location 4300H.
## For Multiplication:
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Multiply A and B using repeated addition.
4.	Store the result in memory locations 4300H and 4301H (if required for higher bits).
## For Division:
1.	Load the dividend from memory location 4200H into register A.
2.	Load the divisor from memory location 4201H into register B.
3.	Perform division using repeated subtraction.
4.	Store the quotient in 4300H and remainder in 4301H.
## Program:
```
; ---------- ADDITION ----------
LDA 8050H     ; Load first number from memory into Accumulator
MOV B, A      ; Move it into Register B
LDA 8051H     ; Load second number into Accumulator
ADD B         ; Add with B
STA 8052H     ; Store result in memory
HLT           ; Halt program


; ---------- SUBTRACTION ----------
LDA 4250H    ; Load first number (minuend) into accumulator
MOV B, A     ; Copy first number into B (save it)

LDA 4251H    ; Load second number (subtrahend) into accumulator
MOV C, A     ; Copy second number into C

MOV A, B     ; Restore first number into accumulator
SUB C        ; A = A - C = (First number - Second number)

STA 4252H    ; Store result at 4252H
HLT          ; Halt program


; ---------- MULTIPLICATION ----------
LDA 2050H      ; Load first number into Accumulator
MOV B, A      ; Store it in B (multiplier)
LDA 2051H      ; Load second number into Accumulator
MOV C, A      ; Store it in C (multiplicand)
MVI A, 00     ; Clear Accumulator for result
LOOP: ADD C   ; Add multiplicand to result
DCR B         ; Decrease multiplier by 1
JNZ LOOP      ; Repeat until multiplier = 0
STA 2052H      ; Store result in memory 2052H
HLT           ; Stop


; ---------- DIVISION ----------
LXI H,0020H ; HL → 0020H
MOV A,M ; A = Dividend
INX H ; HL → 0021H
MOV C,M ; C = Divisor
MVI D,00H ; D = Quotient = 0
L1: CMP C ; Compare A (dividend) with C (divisor)
JC L2 ; If A < C → division complete
SUB C ; A = A - C (subtract divisor from dividend)
INR D ; Increment quotient
JMP L1 ; Repeat until A < C
L2: STA 0023H ; Store Remainder (A) at 0023H
MOV A,D ; A = Quotient
STA 0022H ; Store Quotient at 0022H
HLT ; Stop
```

## Output:
<img width="1910" height="969" alt="Screenshot 2025-08-20 091243" src="https://github.com/user-attachments/assets/5ee0655e-eeaf-4259-8dfe-12f431ce938d" />
<img width="1920" height="1020" alt="Screenshot 2025-08-20 093422" src="https://github.com/user-attachments/assets/4a911744-e702-4164-a12e-ea7f7aaa719b" />
<img width="1920" height="1020" alt="Screenshot 2025-08-20 094041" src="https://github.com/user-attachments/assets/990c427b-a1a9-4943-954e-1747ffdb2fb4" />
<img width="972" height="466" alt="image" src="https://github.com/user-attachments/assets/68e6c5b4-096e-4caf-8ac5-be179b33de31" />





## ➤ Final Output Summary  

| Operation       | Input (Example) | Result (Hex) | Result (Decimal) |
|-----------------|-----------------|--------------|------------------|
| Addition        | 10, 2           | 0CH          | 12               |
| Subtraction     | 10, 2           | 08H          | 8                |
| Multiplication  | 10 × 2          | 14H          | 20               |
| Division        | 10 ÷ 2          | 05H / 00H    | 5 Quotient / 0 Remainder |
## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.

