# Hardcall Reference
This is a complete list of the hardware calls that can be made to virtual hardware, excluding custom hardware.

## 100
```asm
HARDCALL #100
```

This call is used by the IOKit virtual hardware, and tells it to read the IOKit controller and text buffer, and execute the configuration inside of the IOKit controller, and read the contents of the text buffer until a null terminator character has been reached.