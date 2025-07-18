# 3. Registers
Let's say that we tell our computer to compute `1 + 2`. Our CPU is easily capable of figuring out the answer, but the more important question is where will it store it? In Assembly Languages, the results of Arithmetic operations are stored in containers called **registers.**

## What is a register?
A register can be imagined like a box. You can put any numerical value into this box. If you have done any programming before you will already be familiar with **variables**. Variables are the descendants of registers, they both store things. However, there are crucial differences. Firstly, there aren't an infinite number of registers, unlike variables. The number of registers you get varies depending on the computer you are programming for, but on the ASMX VM, there are only **8 registers**. This means you generally have to think smarter about using your registers. Secondly, only **numeric values** can be stored in registers, unlike variables. Thirdly, you cannot name registers, all registers have **predetermined names** that cannot be changed, unlike variables. However on the positive side, the number you can store in a register can be as big as you want (this is only specific to ASMX), and it can be negative or a decimal.

## Which registers are there?
In ASMX, all registers start with a u. Here is a list:

```asm
u1
u2
u3
u4
u5
u6
u7
u8
```
Next, you'll learn about **immediates** before getting to start using registers for the first time!