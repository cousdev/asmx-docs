# 5. Reading Instruction References
So far you've seen a couple of instructions, `SET`, `ADD`, `SUB`, `MUL`, and `DIV`. In ASMX, we use **Instruction References** to describe an instruction's syntax, and the modes it supports. By knowing how to read an Instruction Reference, you will be able to read and understand the syntax of any instruction. An Instruction Reference looks like this:

```asm
SET [r] [i]
```

What does this mean? An Instruction Reference contains two parts:

- An Opcode (like `SET`, `ADD` etc)
- Parameter Descriptors (The letters shown in square brackets)

A parameter descriptor tells you what type of parameter is allowed to be used. The `[r]` descriptor is short for register, and it means the first parameter must be a register. The `[i]` descriptor is short for immediate, and it means the second parameter must be an immediate, like `#10` for example.

---

But `[r]` and `[i]` are not the only types of descriptors that exist, there are many descriptors you will come across. Here is a run through of all of them:

## r
The `[r]` descriptor means register. Only a register (e.g. `u3`) can be given for that parameter.

## i
The `[i]` descriptor means immediate. Only an immediate (e.g. `#10`) can be given for that parameter.

## ri
The `[ri]` descriptor means register or immediate. Either a register or immediate can be given for this parameter. This is common with arithmetic, for example:

```asm
ADD [r] [ri] ; This is an instruction reference, not real code
ADD u1 u2 ; Valid
ADD u1 #13 ; Also valid
ADD #10 #10 ; Invalid, parameter 1 must be a register
```

## label
The `[label]` descriptor refers to a jump label, which you'll learn about more in the Jumps chapter. A label always starts with an @ symbol. For example:

```asm
JMP [label] ; This is the instruction reference for JMP.
JMP @my_label ; This is valid. Labels can be whatever they want, as long as they have an @
JMP my_label ; Invalid, missing an @, so it is therfore not a label.
```

## ra
Not to be confused with `[ri]`, `[ra]` is short for RAM address. You will learn more about RAM in the Memory chapter. A RAM address is the exact same as an immediate, however it is referring to a location in RAM. For example:

```asm
LOAD [r] [ra] ; Instruction reference for LOAD
LOAD u1 #20 ; This is valid, because a RAM address is the same as an immediate.
```

## string
The `[string]` descriptor is only used in macro instructions (you'll learn about them later). A string is basically a sentence, marked using quotation marks. It looks like this:

```asm
"This is a string."
```

---

## Test your knowledge
Now that you know what an Instruction Reference is and how to read one, read this Instruction Reference and think in your mind what each parameter means.

```asm
JEQ [r] [ri] [label]
```

---

If you thought that the first parameter was a register, the second parameter could be either a register or an immediate, and the last parameter must be a label, then well done! Remembering all the different parameter descriptors will take time, but once you've learnt them, you will be able to read an Instruction Reference and instantly know the syntax for that instruction, making your life a lot easier! 

## Takeaways
Here are the key takeaways from this lesson:

- Instruction References are **not code**, they are a way of describing the syntax of an individual instruction.
- Instruction References have two parts, an Opcode and Parameter Descriptors.
- Each Parameter Descriptor has a type, which maps to the type of input which can be given for that parameter.
- Learning the different Parameter Descriptors will allow you to read Instruction References with ease. **Your future self will thank you!**