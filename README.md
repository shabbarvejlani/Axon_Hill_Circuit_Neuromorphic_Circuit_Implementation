# Axon_Hill_Circuit_Neuromorphic_Circuit_Implementation


#Netlist
*Custom Compiler Version S-2021.09
*Sat Feb 26 19:32:37 2022

*.SCALE METER
*.LDD
.GLOBAL gnd!
********************************************************************************
* Library          : axon_hillock_lib
* Cell             : axon_hillock_circuit
* View             : schematic
* View Search List : auCdl schematic
* View Stop List   : auCdl
********************************************************************************
.subckt axon_hillock_circuit GND I_IN VDD VOUT Vb
*.PININFO GND:B I_IN:I VDD:B VOUT:O Vb:I
MM4 I_IN VOUT net21 GND n105 w=0.2u l=0.03u nf=2 m=1
MM5 net21 Vb GND GND n105 w=0.2u l=0.03u nf=2 m=1
MM1 VOUT net16 GND GND n105 w=0.1u l=0.03u nf=1 m=1
MM0 net16 I_IN GND GND n105 w=0.1u l=0.03u nf=1 m=1
MM3 VOUT net16 VDD VDD p105 w=0.1u l=0.03u nf=1 m=1
MM2 net16 I_IN VDD VDD p105 w=0.1u l=0.03u nf=1 m=1
CC7 I_IN GND 'Cmem' $[CP]
CC6 I_IN VOUT 'Cfb' $[CP]
.ends axon_hillock_circuit

********************************************************************************
* Library          : axon_hillock_lib
* Cell             : sim_axon_hillock_circuit
* View             : schematic
* View Search List : auCdl schematic
* View Stop List   : auCdl
********************************************************************************
.subckt sim_axon_hillock_circuit
XI0 gnd! net7 net8 net12 net10 axon_hillock_circuit
RR7 net12 gnd! 10meg $[RP]
.ends sim_axon_hillock_circuit
