# 2. What is Assembly?
Ever since computers were made, programmers have faced a problem. Computer speak in Machine Code (represented as Binary), and Machine Code isn't readable by humans. So in response, programmers built a "translator", which would turn a readable human language, into machine code language. This way, programmers could write in a language that was easy for them to understand, whilst computers could use the machine code language that they understand.

---

These "translators" still exist today, and they are called **assemblers.** And the languages that assemblers translate into machine code are called **assembly languages**. Programming languages like C, Python and even Scratch are all descendants of Assembly Languages, and assemblers quietly work in the background to make all the tech we use every day possible.

## What is a Virtual Machine?
A machine is a pretty vague term, but according to computer scientist John von Neumann, a machine has a CPU, a Memory Unit, Input devices, and Output devices. A Virtual Machine is when we simulate a machine, on a machine. This is achieved by using code to simulate a CPU, memory unit etc. A Virtual Machine is completely capable of doing anything a regular machine can, it can run games and operating systems! Companies like Microsoft run thousands of Virtual Machine's every day!

## So how do we run a VM on Scratch?
Well let's go back to our list, to make a machine, we need:

- A CPU
- A Memory Unit
- Input Devices
- Output Devices

In Scratch, a Memory Unit is just a list. A Scratch List can store 200 000 items, plenty of memory. Input Devices? We have blocks that detect keys and the mouse position. Output Devices? We have the Stage, where we can display anything we want with Sprites and the Pen tool. The CPU? We have blocks that can do arithmetic. In conclusion, there is absolutely no reason why we could not create a Virtual Machine on Scratch.

## The ASMX Virtual Machine
The ASMX Virtual Machine does everything I said above (and more)! With the ASMX VM, we have a programmable computer that can run games, and show videos and more. But this brings us back to the problem I brought up at the beginning. The VM does not speak the same language we do. Like all machines, the VM speaks machine code, and we need an assembler (a translator) to be able to tell our Virtual Machine what to do.

## The ASMX Assembler
The ASMX Assembler translates between Assembly Language, and the ASMX VM's machine code language. There are lots of different assembly languages, because there are lots of different types of computers, however the ASMX assembler only understands ASMX assembly. But just because our assembly language is different than others, most low-level concepts carry over to several different assembly languages.