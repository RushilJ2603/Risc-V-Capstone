# RISC-V 5-Stage Pipelined Processor

![Architecture Diagram](architecture.png)

## Overview
This repository contains the RTL implementation of a 32-bit RISC-V (RV32I) processor using a classic 5-stage pipelined architecture. The design serves as **Phase I** of a larger Capstone project titled *"Heterogeneous Out-of-Order RISC-V SoC: Architecting Dynamic Scheduling & Hardware Acceleration."*

The core is designed in Verilog HDL and verified using Xilinx Vivado. It features a dedicated hazard handling unit to resolve data dependencies via forwarding and control hazards via flushing, ensuring high instruction throughput.

## Project Team
* **Vikram Singh** (241EC164)
* **Rushil Jain** (241EC148)
* **Sonigara Jainam** (241EC155)
* **Somyak Mohanta**

## Key Features
* **ISA Compliance:** RISC-V RV32I Base Integer Instruction Set (supports ~35 instructions).
* **Pipeline Depth:** 5-Stage (Fetch, Decode, Execute, Memory, Writeback).
* **Hazard Management:**
    * **Data Hazards:** Resolved using an Operand Forwarding Unit (resolves RAW hazards without stalling).
    * **Control Hazards:** Handled via flushing with a static "Assume Not Taken" branch prediction strategy.
* **Memory Architecture:** Harvard Architecture (Separate Instruction and Data Memory).
* **Verification:** Behavioral simulation validated with hex-file memory initialization.

## Project Structure

```text
├── pp.xpr                 # Xilinx Vivado Project File
├── pp.srcs/
│   ├── sources_1/new/     # RTL Source Codes
│   │   ├── top_module.v          # Top-level processor module
│   │   ├── hazard_unit.v         # Hazard detection and forwarding logic
│   │   ├── controlpath.v         # Main control unit
│   │   ├── alu.v                 # Arithmetic Logic Unit
│   │   ├── pp_stage_2.v to _5.v  # Pipeline stage registers
│   │   ├── reg_file_.v           # Register File (32 x 32-bit)
│   │   ├── data_mem.v            # Data Memory
│   │   └── instruction.v         # Instruction Memory
│   └── sim_1/new/         # Simulation Files
│       └── testbench.v           # Main Testbench
├── hex_files/             # Memory Initialization Files
│   ├── rv32i_real.hex            # Instruction Memory Hex Code
│   ├── data_mem_file.hex         # Initial Data Memory Values
│   └── register_file_counting.hex
└── architecture.jpg       # High-level Architecture Design
