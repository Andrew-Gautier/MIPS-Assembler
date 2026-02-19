# MIPS-Translatron 3000

A MIPS assembler/disassembler developed for ByteForge Systems to support firmware validation of the Titan‑9 industrial automation unit. This tool converts between assembly instructions and machine code (binary/hex), with robust error handling and a built‑in test bench.

## Features

- **Assembler** – Convert MIPS assembly to 32‑bit machine code (binary and hex).
- **Disassembler** – Convert machine code (binary or hex) back to human‑readable assembly.
- **Supported Instructions**
  - **R‑format**: `ADD`, `SUB`, `AND`, `OR`, `SLT`, `MULT`, `DIV`, `MFHI`, `MFLO`
  - **I‑format**: `ADDI`, `ANDI`, `ORI`, `SLTI`, `LW`, `SW`, `BEQ`, `BNE`, `LUI`
  - *Newly added*: `MULT`, `ORI`, `SLTI`
- **Error Handling** – Clear error messages for invalid registers, immediates, or syntax.
- **Bit Flip Correction** – Tools to identify and correct single‑bit errors in corrupted machine code (Deliverable 2).
- **Test Bench** – Automated verification of all instructions with expected binary/hex outputs (50+ test cases).

## Building

Compile all `.c` files with a C compiler (e.g., gcc):

```bash
gcc -o mips-translatron *.c -I.
```
No external dependencies are required.
## Usage
Run the executable:
```bash
./mips-translatron
```
The menu offers three options:

    1. Assembly to Machine Code – Enter an assembly instruction (e.g., ADD $t1, $t2, $t3) to get its binary and hex representation.

    2. Machine Code to Assembly – Choose between binary or hex input; the tool will output the corresponding assembly.

    3. Test Bench – Runs a comprehensive suite of tests to verify correctness of all instructions. Results show pass/fail per test and a final count.
## Example
> 1
Enter a line of assembly:
> ADD $t1, $t2, $t3
Hex: 0x014B4820    Binary: 0000 0001 0100 1011 0100 1000 0010 0000

## Testing
The test bench (testBench() in MIPS_Interpreter.c) compares generated binary/hex against predefined expected values for every supported instruction, including edge cases (immediate limits, zero registers, etc.). It also verifies that the disassembler correctly reconstructs the original assembly.
## Credits
- Andrew Gautier – Initial refactoring and instruction fixes 
- Shannon Seiler – Documentation, testing, and debugging
- Landon Urcho – Test bench implementation and debugging
- Tyler Wright – Bit‑flip correction and analysis
    
