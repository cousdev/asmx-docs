# Instruction Set Reference
This reference contains a list of all Instructions in ASMX Assembly. This list only contains **base instructions**, if you are looking for macro instructions in specific packages, check the package references. If you do not know how to read Instruction References, check the guide [here.](../guide/Reading%20Instructions.md)

## Arithmetic Instructions
Arithmetic instructions perform mathematical operations on the VM.

### ADD
```asm
ADD [r] [ri]
```
Sets `[r]` to `[r]` plus `[ri]`. For example:
```asm
ADD u1 #6 ; Sets u1 to u1 + 6.
```

### SUB
```asm
SUB [r] [ri]
```
Sets `[r]` to `[r]` minus `[ri]`. For example:
```asm
SUB u2 #10 ; Sets u2 to u2 - 10.
```

### MUL
```asm
MUL [r] [ri]
```
Sets `[r]` to `[r]` multiplied by `[ri]`. For example:
```asm
MUL u3 #20 ; Sets u3 to u3 * 20.
```

### DIV
```asm
DIV [r] [ri]
```
Sets `[r]` to `[r]` divided by `[ri]`. For example:
```asm
DIV u4 #15 ; Sets u4 to u4 / 15.
```

### INC
```asm
INC [r]
```
Sets `[r]` to `[r]` plus one. For example:
```asm
INC u2 ; Sets u2 to u2 + 1
```

### DEC
```asm
DEC [r]
```
Sets `[r]` to `[r]` minus one. For example:
```asm
DEC u6 ; Sets u6 to u6 - 1.
```

### RAND
```asm
RAND [r] [ri] [ri]
```
Sets `[r]` to a random value between the first `[ri]` and the second `[ri]`. For example:
```asm
RAND u7 #15 #u5 ; Sets u7 to a random value between 15 and u5.
```

---

## Memory
Memory instructions allow you to interact with memory hardware, such as registers and RAM. It also allows you to move data between memory hardware.

### SET
```asm
SET [r] [i]
```
Sets `[r]` to `[i]`. For example:
```asm
SET u8 #32 ; Set u8 = 32
```

### MOV
```asm
MOV [r] [r]
```
Sets `[r]` to the second `[r]`. Duplicates/copies the contents of a register into another register. For example:
```asm
MOV u4 u6 ; Sets u4 to the contents of u6.
```

### LOAD
```asm
LOAD [r] [ra]
```
Retrieves data from RAM via the `[ra]` RAM address and stores the data in `[r]`. For example:
```asm
LOAD u4 #20 ; Get value of RAM address 20 and copy it into u4.
```

### STORE
```asm
STORE [ra] [r]
```
Copies data from `[r]` and stores it in RAM Address `[ra]`. For example:
```asm
STORE #13 u5 ; Copy the value of u5 into RAM Address #13.
```

---

## Jumps
Jump commands allow for loops and comparisons, and can act like if-else and for loops.

### JMP
```asm
JMP [label]
```
Jumps to a label. For example:
```asm
JMP @my_label ; Jumps to the part of the code labelled with my_label.

@my_label
... ; Starts running code here.
```

### JLT
```asm
JLT [r] [ri] [label]
```
Jumps to a label if `[r]` is less than `[ri]`. For example:
```asm
JLT u3 #10 @my_label ; If u3 < 10, then jump to my_label.

@my_label
... ; Run code here.
```

### JEQ
```asm
JEQ [r] [ri] [label]
```
Jumps to a label if `[r]` is equal to `[ri]`. For example:
```asm
JEQ u6 #13 @my_label ; If u6 = 13, then jump to my_label.

@my_label
... ; Run code here.
```

### JGT
```asm
JGT [r] [ri] [label]
```
Jumps to a label if `[r]` is greater than `[ri]`. For example:
```asm
JGT u5 #24 @my_label ; If u5 > 24, then jump to my_label.

@my_label
... ; Run code here.
```

---

## Hardware
These commands allow for a bridge between code and hardware. By creating your own hardware on the VM, you can use these commands to interact with the hardware.

### HALT
```asm
HALT
```
Stops the program execution immediately. For example:
```asm
... ; Other instructions
HALT ; Stop all scripts.
```

### HARDCALL
```asm
HARDCALL [i]
```
Sends a hardware call, which is received by a piece of hardware and executed. Code execution is paused until the hardware has finished executing (synchronous). For example:
```asm
HARDCALL #100 ; Sends a hardware call to the IOKit virtual GPU to render the current buffer.
```