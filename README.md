











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
Open ModelSim and set the working directory to the project root.

Create a working library:

Bash
vlib work
Compile all Verilog source modules and the testbench:

Bash
vlog MIPSVerilogWOJALv1/*.v tb_mips.v
Start the simulation:

Bash
vsim work.tb_mips
Add signals to the waveform viewer and run simulation:

Bash
add wave -r /*
run 500ns
License
This project is licensed under the MIT License - see the LICENSE file for details.

How to Commit and Push This README.md to GitHub
Once you save the README.md file inside E:\MIPS_SCP_Assignment, push it to your repository using these commands in PowerShell:

PowerShell
cd "E:\MIPS_SCP_Assignment"
git add README.md
git commit -m "Add detailed README documentation with architecture specs and ModelSim guide"
git push origin main
