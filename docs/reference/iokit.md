# IOKit Reference
This reference describes the IOKit Controller in detail, its hardcall's, as well as the IOKit package's macro instructions.

## IOKit Controller Memory Map
Read further below for more details about each field and its properties.


| Memory Address | Name         | Purpose                                                            |
|----------------|--------------|--------------------------------------------------------------------|
| 1              | Mode         | Which mode the IOKit Virtual Hardware is in.                       |
| 2              | X            | The X position of the render (if applicable).                      |
| 3              | Y            | The Y position of the render (if applicable).                      |
| 4              | Size         | The size of the render (if applicable).                            |
| 5              | Text Pointer | The address in RAM of where the text value is or should be stored. |
| 6              | Text Spacing | The spacing of each letter of text (if applicable).                |


## IOKit Modes
The IOKit virtual hardware can be put in different modes, each mode corresponding to a different command to execute. The mode corresponds to:

- Text output mode is represented as **mode 1**.
- Text input mode is represented as **mode 2**.

### Text Output Mode
When the IOKit virtual hardware is placed in Text Output mode, the virtual hardware will read the RAM starting at the text pointer, and write each letter in the RAM until a null terminator character is reached. This text will be rendered at the X and Y, as well as at Size (100% is the default), with the text spacing (10 is the recommended value).

### Text Input Mode
When the IOKit virtual hardware is placed in Text Input mode, the virtual hardware will lock execution of the code, record and write keypresses from the user onto the screen at X, Y, with the Size and Spacing. When the Enter key is pressed, the text that was recorded will be written into the Text Pointer, and code execution will resume.

---

## IOKit Package Macros
All installations of ASMX come with the IOKit package by default as **part of the standard library**. All IOKit package macros are under the namespace `io`. By using these macros, they can automatically configure the IOKit controller, write text into the buffer, etc.

### IO CONFIG
```asm
IO CONFIG <x [i]> <y [i]> <size [i]> <spacing [i]>
```

This macro configures the IOKit controller (apart from the mode and text pointer), in one command. For example:

```asm
IO CONFIG #-221 #150 #100 #10 ; Set the controller to X: -221 Y: 150, with default size (100) and default spacing (10).
```

### IO TEXT
```asm
IO TEXT <text pointer [ra]> <text [string]>
```

This macro sets the IOKit controller's mode to 1, writes the text into the text pointer, adds a null terminator, then writes the text with `HARDCALL #100`. For example:

```asm
IO TEXT #10 "Hello" ; Writes the word Hello into RAM starting at address 10, going up. 
                    ; It then sets the controller mode to 1, then executes the virtual hardware.
```

### IO INPUT
```asm
IO INPUT <text pointer [ra]>
```

This macro sets the IOKit controller's mode to 2, and then locks execution and starts rendering keypresses onto the screen. When enter is pressed, the string is then written into the text pointer, and code execution resumes. For example:

```asm
IO INPUT #50 ; Get user input and put it in RAM address 50.
```

## Hardcalls
Configuring the IOKit controller alone does not trigger the virtual hardware to begin rendering. Instead, the virtual hardware listens for a hardcall to be made from the code. Hardcalls only need to be done manually if you **are not using macros.** Macros automatically handle hardcall's for you.

### 100
A hardcall with the immediate of 100 will trigger the virtual hardware to read the controller configuration, and execute that configuration. For example, if you have set up the controller to write text to the screen, and entered text in the buffer, then this hardcall will execute that command.