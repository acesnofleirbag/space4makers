# Assembly

Each architecture has your own operation code (opcode) that is an instruction set supported by the processor arch

### Processor

The processor has the following steps:

```
- fetch
- decode
- exec cycle
```

### Cheatsheets

- The instruction i++ otherwise ++i use one more instruction on generated assembly code, for a simple increment
    outside a for block for instance. Inside a for block the generated asm were the same
- Syscall numbers can be found on `/usr/include/asm/unistd.h`
