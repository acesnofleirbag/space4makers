### Alignment

- Why I need to make the memory alignment?

The reason for this is that the processor requires two memory accesses to make an unaligned memory access; aligned
accesses require only one memory access. A word (2-byte) or doubleword (4-byte) operand that crosses a 4-byte boundary
or a quadword (8-byte) operand that crosses an 8-byte boundary is considered unaligned and requires two separate memory
bus cycles for access
