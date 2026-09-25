Markdown# MIPS Single-Cycle Processor (Verilog HDL)

A complete 32-bit **MIPS Single-Cycle Processor** implemented in Verilog HDL. This repository contains the digital logic design, module decompositions, control unit mapping, custom testbenches, and an integrated assembler tool for hardware simulation and verification in **ModelSim / EDA Playground**.
Architecture OverviewThe single-cycle processor executes every instruction within a single clock cycle ($CPI = 1$). The datapath routes instructions from memory fetch through register decode, ALU execution, memory access, and register write-back.Major Datapath ComponentsProgram Counter (PC): 32-bit register tracking the current instruction address, updated on the positive clock edge (PC_next = PC + 4 or branch address).Instruction Memory: Read-only memory storing 32-bit machine code instructions.Register File: $32 \times 32$-bit register array supporting simultaneous asynchronous dual-register reads and synchronous single-register writes.Control Unit: Decodes opcode bits [31:26] to generate global multiplexer and control signals.ALU & ALU Control: Computes arithmetic, logical, and address offset operations based on function field bits [5:0] and ALUOp.Data Memory: Synchronous read/write RAM for memory access (lw / sw).Supported Instruction Set Architecture (ISA)TypeInstructionOpcode / Funct (Hex)DescriptionR-Typeadd0x00 / 0x20Add registers: rd = rs + rtR-Typesub0x00 / 0x22Subtract registers: rd = rs - rtR-Typeand0x00 / 0x24Bitwise AND: rd = rs & rtR-Typeor0x00 / 0x25Bitwise OR: rd = rs | rtR-Typeslt0x00 / 0x2ASet on less than: rd = (rs < rt) ? 1 : 0I-Typelw0x23Load word: rt = Memory[rs + sign_ext(imm)]I-Typesw0x2BStore word: Memory[rs + sign_ext(imm)] = rtI-Typebeq0x04Branch if equal: if (rs == rt) PC = PC + 4 + (imm << 2)Control Unit Signal MappingInstructionRegDstALUSrcMemtoRegRegWriteMemReadMemWriteBranchALUOpR-Type100100010lw011110000swX1X001000beqX0X000101Project StructurePlaintext.
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
Simulation & Testing (ModelSim)Open ModelSim and set the working directory to the project root.Create a working library:Bashvlib work
Compile all Verilog source modules and the testbench:Bashvlog MIPSVerilogWOJALv1/*.v tb_mips.v
Start the simulation:Bashvsim work.tb_mips
Add signals to the waveform viewer and run simulation:Bashadd wave -r /*
run 500ns
LicenseThis project is licensed under the MIT License - see the LICENSE file for details.How to Commit and Push This README.md to GitHubOnce you save the README.md file inside E:\MIPS_SCP_Assignment, push it to your repository using these commands in PowerShell:PowerShellcd "E:\MIPS_SCP_Assignment"
git add README.md
git commit -m "Add detailed README documentation with architecture specs and ModelSim guide"
git push origin main
