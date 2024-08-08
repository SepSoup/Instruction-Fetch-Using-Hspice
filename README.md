# Instruction Fetch Stage in Patterson Processing Model

## Overview

The instruction fetch stage is a critical component of the Patterson processing model, which describes the operation of a CPU's instruction cycle. This README provides a detailed explanation of how the instruction fetch stage works and how it can be simulated using HSPICE, a hardware simulator. It also includes information about global settings and power supplies for a comprehensive understanding.
This program aims to fetch each the Instructions of the Fibonacci program sequentialy with each clock

<img src="https://github.com/SepSoup/Instruction-Fetch-Using-Hspice/blob/main/Patterson%20Processor%20Fetch/Fibonacci%20Program.jpg" alt="Game Logic" width="600"/>


## Patterson Processing Model: Instruction Fetch Stage

The instruction fetch stage is the first step in executing an instruction and involves several key components:

### Key Components


<img src="https://github.com/SepSoup/Instruction-Fetch-Using-Hspice/blob/main/Patterson%20Processor%20Fetch/Map.jpg" alt="map" width="600"/>


1. **Program Counter (PC):**
   - **Purpose:** Holds the address of the next instruction to be fetched.
   - **Operation:** Incremented after each fetch to point to the subsequent instruction. Can be modified by branch instructions or control flow changes.

2. **Instruction Memory (IM):**
   - **Purpose:** Stores the program instructions to be executed.
   - **Operation:** Retrieves the instruction located at the address specified by the PC.

3. **Clock Signal:**
   - **Purpose:** Synchronizes the fetch operation and other CPU activities.
   - **Operation:** Pulses at regular intervals to control PC updates and instruction fetching.

4. **Instruction Register:**
   - **Purpose:** Temporarily holds the fetched instruction.
   - **Operation:** Passes the instruction to the next stage of the pipeline for further processing.

### Detailed Operation

1. **PC Initialization:**
   - At the start of execution or after a reset, the PC is set to the address of the first instruction.

2. **Fetching the Instruction:**
   - **Clock Cycle Trigger:** The PC's current value is used to fetch the instruction from IM on each clock cycle.
   - **Addressing:** The address from the PC is sent to IM, which retrieves the corresponding instruction.
   - **Instruction Delivery:** The fetched instruction is loaded into an instruction register for decoding and execution.

3. **Updating the PC:**
   - **Incrementing:** After the instruction is fetched, the PC is incremented to point to the next instruction.
   - **Handling Branches:** For branch instructions, the PC is updated to a new address based on branch logic.

4. **Clock Signal Role:**
   - Ensures that fetching, PC incrementing, and instruction loading occur in a synchronized manner.

## Simulation with HSPICE

In an HSPICE simulation, the instruction fetch stage can be modeled as follows:

### Global Settings

1. **Simulation Time:**
   - Set the total simulation time to cover multiple clock cycles to observe the fetching process over time.

2. **Time Step:**
   - Define the time step for the simulation to accurately capture the behavior of each clock cycle.

3. **Temperature and Process Variations:**
   - Configure settings to simulate variations in temperature and process parameters if necessary for more accurate results.

### Power Supplies

1. **Voltage Sources:**
   - **VDD:** Provide the supply voltage for the circuit components `(typically 1.8V, 3.3V, or according to the specific technology used)`.
   - **Ground:** Ensure a stable `ground` reference for all circuit components.

2. **Power Supply Decoupling:**
   - Use decoupling capacitors to filter out noise and stabilize the power supply to sensitive components like the PC and IM.

### Simulation Process

1. **Setup:**
   - Define the `PC` and `IM` as circuit elements.
   - Use a `clock` signal to drive timing for instruction fetching.

2. **Configuration:**
   - Set the global simulation settings, including time, time step, and temperature/process variations.
   - Connect power supplies to the circuit elements and configure decoupling.

3. **Simulation Execution:**
   - **Initialization:** Set the starting address in the PC and load instructions into IM.
   - **Clock Pulses:** Each clock pulse triggers instruction fetching based on the PC value.
   - **Instruction Fetch:** Instructions are retrieved and the PC is updated.
   - **Iteration:** The process repeats with each clock cycle, simulating sequential instruction fetching.
  
## Visualization with CScope

we can see how this hardware will act in the given sceanario by visualizing it with CScope :

- **Expected output :**
  
| number    |  HEX       |
|-----------|------------|
| 1         | 20040001   |   
| 2         | 2005FFFF   |
| 3         | 10600004   |
| 4         | 00852822   |
| 5         | 00852822   |
| 6         | 2063FFFF   |
| 7         | 08000003   |
| 8         | A00400FF   |

## Cscope output

<img src="https://github.com/SepSoup/Instruction-Fetch-Using-Hspice/blob/main/Patterson%20Processor%20Fetch/Output%20Graph.png" alt="Graph" width="600"/>



## Summary

The instruction fetch stage in the Patterson processing model ensures that instructions are sequentially retrieved from memory. It involves the PC, instruction memory, and clock signal to control the process. Global settings and power supplies are crucial for accurate HSPICE simulation. Proper configuration of these elements helps in accurately modeling and analyzing the instruction fetch stage.

For further information or assistance, please refer to the [Patterson and Hennessy Computer Organization and Design](https://www.elsevier.com/books/computer-organization-and-design/patterson/978-0-12-407726-3) or consult HSPICE documentation.

