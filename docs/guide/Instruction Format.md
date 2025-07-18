# 4. Instruction Format
Let me introduce you to the first instruction that you'll learn in ASMX!

```asm
SET u1 #10
```

This is the `SET` command! Notice how the word `SET` is uppercase? This is because `SET` is the "opcode". An opcode is a code to the CPU that tells it which operation should be performed. In ASMX, it is not strictly necessary to put opcodes uppercase, but it is common. You will also notice a register, `u1`. But what is that thing with the hashtag? That is called an immediate. Let's break this instruction down.

## The Opcode

In most assembly languages, the first part of an instruction is the Opcode. Think of instructions like this:

```asm
<opcode> <parameter_1> <parameter_2> ...
```

The opcode in our instruction is `SET`. The `SET` command will set a registers value to an immediate. You'll learn what an immediate is next. The syntax for `SET` looks like this:

```asm
SET <register> <immediate>
```

## The Register
The register in this case is `u1`. All registers begin with a u (in ASMX), so registers are pretty identifiable.

## The Immediate
The immediate in this case is `#10`. All immediates begin with a hashtag. The instruction in full is setting the `u1` register to 10. But immediates aren't just used in the `SET` instruction, they're used in most arithmetic instructions (and jumps, you'll learn about them later).

## Uses of Immediates
Immediates are mostly use when doing arithmetic. In ASMX, we have 4 different maths operations:

```asm
ADD u1 #5
```
This piece of code sets the `u1` register to itself plus 5.
The same can be applied to all the other operations:
```asm
SUB u2 #10
MUL u4 #32
DIV u7 #9
```

In simple terms, an immediate is **just a number**. You can use that number to set registers, or perform arithmetic (there are other uses of immediates you'll learn later as well). I also want to clarify that in some instances, you can use an immediate or register. This is valid as well:

```asm
ADD u1 u2 ; Sets u1 = u1 + u2
```

## Comments
In ASMX comments are written with a **semicolon**, as shown above. Anything after the semicolon is ignored. There are no multi-line comments in ASMX.

## Takeaways
Hopefully this chapter gave you a general idea of what instructions in ASMX look like. Here is a summary of what is most important:

- Opcodes tell the CPU which operation to perform, and they're generally uppercase e.g. `SET`
- Opcodes are followed by parameters, which can be registers, or immediates.
- Immediates start with a hashtag, and are numbers.
- Comments are written with a semicolon

In the next chapter, I will teach you how to read Instruction References, which will allow you to read and learn about new instructions.