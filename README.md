# Analysis and Mitigation of Side-Channel Vulnerabilities in FPGA-Based AES Design

### Project Description
This project focuses on the security of hardware-based cryptographic systems. Even though the AES-128 algorithm is mathematically secure, its physical implementation on hardware like FPGAs can "leak" sensitive information through power consumption. This project demonstrates how an attacker can use Correlation Power Analysis (CPA) to recover secret cryptographic keys by monitoring these power fluctuations. To solve this, we designed and implemented a secure AES-128 core using Boolean Masking, which randomizes intermediate data to ensure that power consumption no longer correlates with the secret key, effectively neutralizing the side-channel threat.

---

## Project Overview
* Objective: To evaluate the susceptibility of unprotected AES-128 cores to side-channel attacks and implement a secure Verilog-based masked AES core.
* Target Platform: ChipWhisperer CW305 (Artix-7 FPGA).
* Analysis Tool: ChipWhisperer Husky.
* Countermeasure: First-order Boolean Masking.

## Key Features
* Key Recovery Attack: Successful extraction of the full 128-bit AES key from an unprotected core using power traces.
* Secure Implementation: A custom Verilog implementation of AES-128 with first-order Boolean masking that randomizes intermediate states to decorrelate power consumption from sensitive data.
* Comparative Analysis: Rigorous validation showing that while the unprotected core leaked the full key, the masked core successfully defeated the attack.

## Hardware and Software Setup
### Hardware
* ChipWhisperer Husky: For high-speed power trace acquisition and synchronized triggering.
* CW305 FPGA Target Board: Running the AES-128 Verilog implementation.
* SMA/20-pin Cables: For power measurement and control signals.

### Software
* Vivado Design Suite: For synthesis, implementation, and bitstream generation.
* Python (Jupyter Notebooks): For controlling the ChipWhisperer hardware and performing statistical CPA analysis.
* Verilog HDL: For hardware design of the AES cores.

## Project Structure
* aes_core.v: The standard, unprotected AES-128 datapath.
* masked_aes.v: The secure AES core incorporating Boolean masking logic.
* cw305_top.v: Top-level module for FPGA interfacing.
* Analysis/: Jupyter notebooks containing the CPA attack and validation scripts.

## Experimental Results
| Implementation | Attack Type | Result |
|----------------|-------------|--------|
| Unprotected AES| First-Order CPA | Full Key Recovered |
| Masked AES     | First-Order CPA | Attack Failed (Security Verified) |

## Future Scope
* Higher-Order Masking: Implementing threshold or multi-share schemes to resist Second-Order CPA attacks.
* TRNG Integration: Replacing pseudo-random masks with a True Random Number Generator.
* Multi-Channel Analysis: Evaluating electromagnetic (EM) and timing side-channels.

## Contributors
* Vankdoth Sahithi Sree
* Karamthot Venkatesh 
* Sushant 

Supervisor: Dr. Vijaypal Singh Rathor
Institution: ABV-Indian Institute of Information Technology and Management (IIITM), Gwalior
