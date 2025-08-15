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

python SICXE.py

