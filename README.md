

Markdown
# MIPS Single-Cycle Processor (Verilog HDL)

A complete 32-bit **MIPS Single-Cycle Processor** design implemented in Verilog HDL. This repository includes core datapath modules, control decoding logic, an assembly tool, and ModelSim simulation scripts.
Project Structure
Plaintext
.
├── Assembler/               # MIPS assembly to machine code hex converter tool
├── MIPSVerilogWOJALv1/      # Core Verilog source modules
│   ├── alu.v                # Arithmetic Logic Unit
│   ├── alu_control.v        # ALU function field decoder
│   ├── control_unit.v       # Main opcode decoder
│   ├── datapath.v           # Datapath register and bus routing
│   ├── data_memory.v        # RAM storage module
│   ├── instruction_mem.v    # Instruction ROM module
│   ├── register_file.v      # 32x32-bit register file ($0-$31)
│   └── mips_top.v           # Top-level single-cycle CPU instantiation
├── work/                    # ModelSim compiled library cache
└── tb_mips.v                # Testbench file for waveform simulation
Simulation & Testing (ModelSim)
To simulate and test the processor using ModelSim, follow these terminal steps:

Open ModelSim and set the working directory to the project root directory (E:\MIPS_SCP_Assignment).

Create a working compilation library:

Bash
vlib work
Compile all Verilog source files and the testbench module:

Bash
vlog MIPSVerilogWOJALv1/*.v tb_mips.v
Start the simulation environment:

Bash
vsim work.tb_mips
Add all top-level signals to the waveform viewer and run for 500ns:

Bash
add wave -r /*
run 500ns
License
This project is licensed under the MIT License - see the LICENSE file for details.

How to Commit & Push to GitHub
To save this file and push it directly to your remote repository branch on GitHub, run these commands in PowerShell:

1
Navigate into local project directory
PowerShell
cd "E:\MIPS_SCP_Assignment"
2
Stage the new README file
PowerShell
git add README.md
3
Commit staged changes
PowerShell
git commit -m "Add detailed README documentation with project structure and ModelSim guide"
4
Push commit to remote repository
PowerShell
git push origin main
