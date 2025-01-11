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

![fp_placed_io](https://github.com/user-attachments/assets/b22da1b9-8bc1-4289-bb86-4a1ba948a556)

![fp_pdn](https://github.com/user-attachments/assets/db1d64b8-386d-4c0a-876b-2e46e63bab98)

![fp_with_pdn](https://github.com/user-attachments/assets/49199bb4-d20f-40ef-b0a8-72cc357bc958)

![fp_with_pdn_CLOSER](https://github.com/user-attachments/assets/84f915e6-ffab-4c9f-bdfc-be4106d85bdd)


### Placement 

![pl_global](https://github.com/user-attachments/assets/3df09ea2-426d-44ba-9152-bab168384019)

![pl_detailed](https://github.com/user-attachments/assets/83cb00ef-0782-4c67-b095-4542fd8489a1)


### Routing

![routing_detailed_MAGIC](https://github.com/user-attachments/assets/bc4e83e4-919b-47dd-acc8-37f923be6afd)


## GDS

![Round_Robin_Arbiter gds](https://github.com/user-attachments/assets/2ab2b230-4ae3-46df-8b0e-3a093de5cc77)

![GDS](https://github.com/user-attachments/assets/bd811ae9-3203-4108-8f83-99ed26a2842f)




## References
[1] M. H. Khan, P. Podder, M.M. Rahman, T. Rahman, T. Zaman, “DESIGN OF A ROUND ROBIN ARBITER ON RESOURCE SHARING”, Proceedings of 8th IRF International Conference, 04th May-2014, Pune, India, ISBN: 978-93-84209-12-4

## Credits

1 - Verilog HDL Project | Round Robin Arbiter(with code) | EDA Playground | Verilog([https://www.youtube.com/...] - (https://youtu.be/X6oJn7r9-8s?si=NqqBWbNTpkPs7mwc))

Channel: Arjun Narula - ([https://www.youtube.com/channel/...](https://www.youtube.com/@ArjunNarula1122))
The concept of round-robin arbitration and the initial code for this project were adapted from his instructional video.
