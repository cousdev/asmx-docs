# Registers Reference
This contains all the different registers, including auto-registers. In total, there are **12 registers**.

## User-space registers
There are **8 user-space registers**, each starting with the letter `u`. There is no difference between each register, they are all the exact same. Each register may only contain a numerical value, however there is no limit to the size of that value. Each user-space register is listed below:

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
## Auto-registers
Auto-registers are registers that only **macro-generated code can access**. Each auto-register starts with the letter `a`. Trying to access an auto-register in user-space code will result in an error. There are only 4 auto-registers. Auto-registers may only contain a numerical value, however there is no limit to the size of that value. Each auto-register is list below:

```asm
a1
a2
a3
a4
```