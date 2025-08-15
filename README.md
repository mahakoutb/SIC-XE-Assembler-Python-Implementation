* SIC/XE Assembler – Python Implementation
This project is a Python-based assembler for the SIC/XE (Simplified Instructional Computer – Extended) architecture. It processes assembly source code and generates object code in HTE (Header, Text, End) format, making it suitable for educational use, compiler labs, or system-level tool development.

📚 Table of Contents
🔁 pass1 – Build Symbol Table
🔄 pass2 – Generate Object Code
🧾 HTE_Record – Output HTE Format
🔑 Key Functions
🔁 pass1()
Builds the symbol table and assigns memory locations to each line in the source program.

🔄 pass2()
Generates object codes for each instruction using proper format and addressing mode (immediate, indirect, PC-relative, base-relative, etc.).

🧾 HTE_Record()
Produces the HTE format output, including:

H (Header) record with program name, starting address, and length.
T (Text) records split into 30-byte segments.
M (Modification) records for format 4 instructions.
E (End) record with program starting address.
* Features
Two-pass assembler architecture.
Supports:
Instruction formats: Format 1, Format 2, Format 3, and Format 4.
Addressing modes: Immediate (#), Indirect (@), Indexed (,X), PC-relative, and Base-relative.
Uses a BASE directive for base-relative addressing.
Supports both numeric literals and symbolic labels.
* Output Example
H^XXCOPY^000000^001077 T^000000^1E^141033^681033^... M^001006^05 M^001014^05 E^000000

yaml Copy Edit

* Purpose
This assembler demonstrates the internal steps of converting assembly language into object code, mimicking real-world assembler behavior for SIC/XE systems. It's built for learning, experimentation, and modular enhancement.

* Educational Use
You can use this project to:

Understand how assemblers resolve symbols and addresses.
Practice implementing instruction decoding and encoding.
Generate and verify machine-level object code.
Explore base-relative and PC-relative addressing computations.
* Quick Start
Ensure you have:

A file Input.xlsx containing the source program.
A file OP_Code_ref.xlsx containing opcode reference data.
Run the notebook or script to:

python SICXE.ipynb

Algorithm – SIC/XE Two-Pass Assembler

Load Input Data
1.1 Read opcode reference table (OP_Code_ref.xlsx).
1.2 Read assembly source program (Input.xlsx).
1.3 Normalize column names (Instruction, Reference).

Pass 1 – Assign Addresses & Build Symbol Table
2.1 Initialize location_counter = 0.
2.2 For each instruction:
- Determine instruction Format from opcode table or directives.
- Increment location_counter according to format or directive size.
- Record the Location for the current line.
2.3 For each labeled line, add {label: location} to SymTable.

Pass 2 – Generate Object Codes
3.1 Assign opcodes to instructions (ignore directives).
3.2 Format 1: Object code = opcode.
3.3 Format 2: Convert registers to numeric codes, build opcode+regs.
3.4 Directives: Mark No_Object_Code for RESB, RESW, START, END, BASE.
3.5 BYTE (hex): Remove X'...' and store hex value.
3.6 BYTE (char): Convert each char to ASCII hex.
3.7 WORD: Convert value to 6-digit hex.

Addressing Modes & Flags
4.1 Set N and I flags (immediate #, indirect @, or both).
4.2 Set X flag for indexed ,X.
4.3 Set B, P, E flags:
- Format 4: E=1, B=0, P=0.
- Format 3: PC-relative if displacement in range; else base-relative.
4.4 Calculate address/disp from symbol table or immediate constant.

Assemble Final Object Code
5.1 Combine opcode (6 bits) + flags (n,i,x,b,p,e) + address/disp into binary.
5.2 Convert binary to hex for final Object_Code.

Generate HTE Records
6.1 H Record: Program name, start address, length.
6.2 T Records: Object codes in 30-byte blocks.
6.3 M Records: For format 4 modifications.
6.4 E Record: Program starting address.

Output
7.1 Display symbol table, object codes, and HTE format output.

