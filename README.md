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

STA 4252H    ; Store result at 4152H
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
LXI H,0020H
MOV A,M
INX H
MOV C,M
MVI D,00H
DIV_LOOP: CMP C
JC DIV_END
SUB C
INR D
JMP DIV_LOOP
DIV_END: STA 0025H
MOV A,D
STA 0024H

HLT
```

## Output:
<img width="1910" height="969" alt="Screenshot 2025-08-20 091243" src="https://github.com/user-attachments/assets/36bdd3c3-71a9-4d0d-a768-9f35e4db6f69" />
<img width="1920" height="1020" alt="Screenshot 2025-08-20 093422" src="https://github.com/user-attachments/assets/b0939650-45c4-4537-b70f-0afe30202bfa" />
<img width="1920" height="1020" alt="Screenshot 2025-08-20 094041" src="https://github.com/user-attachments/assets/243e08f2-265e-4ea2-bde7-7a4808bc0cd6" />
<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/680da28d-396b-4051-b342-8bb736308c33" />




## ➤ Final Output Summary  

| Operation       | Input (Example) | Result (Hex) | Result (Decimal) |
|-----------------|-----------------|--------------|------------------|
| Addition        | 10, 2           | 0CH          | 12               |
| Subtraction     | 10, 2           | 08H          | 8                |
| Multiplication  | 10 × 2          | 14H          | 20               |
| Division        | 10 ÷ 2          | 05H / 00H    | 5 Quotient / 0 Remainder |
## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.
## Output:
## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.
