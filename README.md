# Round-Robin-Arbiter

## Introduction: 
## Round-robin Arbitration 
It's a technique typically used for arbitration for shared resources, load balancing, queuing systems, and resource allocation.
The basic algorithm of round-robin arbitration implies that once a requester has been served he would “go around” to the end of the line and be the last to be served again.

#### FlowChart
![RRA_FlowChart](https://github.com/user-attachments/assets/e9b4a297-c99c-4282-a5af-1ad993ee3364)

## Importance of Round-robin Arbitration in Processors
* Used as a fair (non-starvation) scheduling policy in many computer applications, either implemented in software as part of an operating system or in hardware, especially for real-time applications.
* Provides predictable latency for requests. This is helpful for time-sensitive applications in digital and embedded systems where consistent response times are required.
* Requires less complex hardware than other algorithms like weighted or priority-based arbitration. This simplicity translates into lower resource overhead
* Distribute the workload evenly by systematically rotating access, helping maintain system stability under varying load conditions.


## Project Workflow
Designing an arbiter involves 3 basic steps:

1 - Modeling

2 - Logic verification 

3 - Mapping to Technology Process

### Block Diagram
![RRA_BlockDiagram](https://github.com/user-attachments/assets/a49a18c8-72b8-43a6-a5f9-2b9a140e2dbe)

## Project Overview and Tools
Design is first modelled and represented in a block diagram. 

The model is then described in Verilog HDL and the logic is then verified and simulated by using Xilinx Vivado 2024.1 with Kintex-7 family

Finally, the design is mapped into Google skywater130pdk using Opnelane flow, and the layout for floorplan is obtained. The layout is viewed in the Magic tool.




### Schematics
![RRA_RTL_Schematic](https://github.com/user-attachments/assets/3dcfa1c2-2ca9-4cfe-ae2a-77b23dbee201)
![RRA_Implementation_Schematic](https://github.com/user-attachments/assets/94cc84af-33de-49ab-97ae-59e1f684a09c)

## Simulation Waveform for 4 requests
![RRA_Waveform](https://github.com/user-attachments/assets/9b7610e2-c96b-4e85-badb-093f016876cb)




## Technology Mapping to Google skywater130pdk
Using Openlane Flow to perform synthesis and further steps.

##### Tools used in each stage of Openlane Flow:

#### Synthesis:
* Yosys
* abc (within Yosys)

#### Floorplanning:
* OpenROAD
* FastRoute
* PDN (Power Distribution Network tool)

#### Placement:
* RePlAce
* OpenDP (OpenROAD’s Detailed Placement tool)

#### Clock Tree Synthesis (CTS):
* TritonCTS

#### Routing:
* FastRoute
* TritonRoute
* SPEF-Extractor

### Floorplans
After performing successful synthesis and generating a netlist, floorplanning is performed and the following layout is obtained in the Magic Layout tool. 

![RRA_Floorplan](https://github.com/user-attachments/assets/9a046c01-d38d-4187-b259-8cb15c2086d0)

![RRA_Floorplan_II](https://github.com/user-attachments/assets/05fa7298-e384-495a-8ae3-a0d45b63167c)

![RRA_Floorplan_closer](https://github.com/user-attachments/assets/bef2b24c-49da-4880-981d-fe0c1c672784)

## Current Challenges

I'm currently working on the placement stage of the flow and facing a challenge with its execution. Mentione below. 
If you have experience in this area, I’d appreciate any suggestions or insights.

N.B. I tried tweaking the config.tcl file with the below changes but to no help. 
```bash
set ::env(FP_CORE_UTIL) 45
set ::env(PL_TARGET_DENSITY) 0.85
set ::env(FP_SIZING) "relative"
```

Feel free to open an issue or submit a pull request if you have ideas on how to address this.

### Placement and Routing
While running placement on the design an Error is thrown which is shown below.

![RRA_ERROR_in_Placement](https://github.com/user-attachments/assets/3ccd6aa6-eb1e-4bd3-b257-b5487a56a84b)




## References
[1] M. H. Khan, P. Podder, M.M. Rahman, T. Rahman, T. Zaman, “DESIGN OF A ROUND ROBIN ARBITER ON RESOURCE SHARING”, Proceedings of 8th IRF International Conference, 04th May-2014, Pune, India, ISBN: 978-93-84209-12-4

## Credits

1 - Verilog HDL Project | Round Robin Arbiter(with code) | EDA Playground | Verilog([https://www.youtube.com/...] - (https://youtu.be/X6oJn7r9-8s?si=NqqBWbNTpkPs7mwc))

Channel: Arjun Narula - ([https://www.youtube.com/channel/...](https://www.youtube.com/@ArjunNarula1122))
The concept of round-robin arbitration and the initial code for this project were adapted from his instructional video.
