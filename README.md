# Overview
This project implements a Built-In Self-Test (BIST) enabled SPI Master-Slave communication system designed in Verilog HDL.

The system integrates:

- 8-bit full-duplex SPI protocol

- LFSR-based Pseudo Random Pattern Generator (PRPG)

- Modified MISR/Test Response Analyzer (TRA)

- Embedded Circuit Under Test (CUT)
 
The goal of the project is to enable autonomous self-testing of SPI communication logic without relying on expensive external Automatic Test Equipment (ATE).

# Objectives
* Design a functional 8-bit SPI Master-Slave architecture.

* Embed a BIST mechanism within the SPI system.

* Detect single stuck-at faults using PRPG and MISR.

* Reduce switching power during test mode using bit-swapped LFSR.

* Optimize test application time.

* Validate functionality through RTL simulation.

# Tools & Technologies

* Verilog HDL

* Xilinx ISE / Vivado

* RTL Simulation

* Waveform Analysis

* FPGA-based synthesis 

# System Architecture

The design consists of the following major blocks:

1️⃣ SPI Master

* Generates clock (SCK)

* Controls Slave Select (SS)

* Handles MOSI data transmission

* Receives MISO data

2️⃣ SPI Slave

* Receives MOSI input

* Performs internal processing via CUT

* Sends response through MISO

3️⃣ BIST Architecture

The BIST structure includes:

* TPG (Test Pattern Generator)
Implemented using LFSR to generate pseudo-random test vectors.

* CUT (Circuit Under Test)
Embedded logic block inside the SPI slave module.

* TRA (Test Response Analyzer)
MISR-based signature analyzer that compares actual and expected outputs.

* BCU (BIST Controller Unit)
Controls test enable signals and test flow sequencing.

# Key Technical Features

* 8-bit full-duplex SPI communication

* LFSR generates maximal-length sequence (2ⁿ − 1 states)

* Bit-swapped LFSR reduces switching activity

* Detection of single stuck-at faults

* Test completion in:

  * (k + 5) clock cycles (combinational faults)

  * (2d + 6) clock cycles (remaining FSR faults)

* Up to 25% switching power reduction during test mode

# Verification Strategy

The verification flow includes:

* Directed test cases for SPI communication

* Validation of CPOL/CPHA behavior

* Fault injection scenarios for stuck-at fault detection

* Signature comparison for pass/fail validation

* Simulation waveform analysis

Testbench validates:

* MOSI to MISO data integrity

* Clock synchronization

* Correct test-mode switching

* Signature correctness under fault conditions

# Low Power Testing Strategy

* To reduce excessive switching during BIST:

* Implemented bit-swapping technique in LFSR

* Reduced transition density during test mode

* Achieved up to 25% reduction in switching activity

* Maintained minimal area overhead
# Fault Model Used

- Single Stuck-at Fault Model (SA-0 / SA-1)

- Combinational and sequential fault detection

- Signature-based response compaction using MISR

# Learning Outcomes

Through this project, the following concepts were practically implemented:

* SPI protocol design

* Design-for-Testability (DFT)

* BIST architecture

* LFSR & MISR theory

* Fault modeling

* RTL verification methodology

* Low-power test optimization

# Future Enhancements

* Extend to multi-slave SPI architecture

* Integrate scan-chain based DFT

* Add SystemVerilog/UVM verification environment

* Perform formal verification

* Measure real power using FPGA implementation

* Add fault coverage reporting automation
