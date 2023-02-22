# VSD-IAT-sign-off-timing_sta


OpenSTA is a gate level static timing verifier. As a stand-alone executable it can be used to verify the timing of a design using standard file formats like :-

-Verilog netlist
-Liberty library
-SDC timing constraints
-SDF delay annotation
-SPEF parasitics

OpenSTA is architected to be easily bolted on to other tools as a timing engine.

By using a network adapter, OpenSTAcan access the host netlist data structures without duplicating them.

Query based incremental update of delays, arrival and required times & Simulator to propagate constants from constraints and netlist tie high/low

Reference for commands used in OpenSTA :


https://github.com/ajay18434/VSD-IAT-sign-off-timing_sta/files/10800297/OpenSTA.pdf

Lab_1 : Inputs to OpenSTA


https://user-images.githubusercontent.com/119410034/220531836-426285fb-8988-4399-bbdb-da2df6213f7d.png

Liberty File : Standards Cells Information is present in liberty or .lib file


https://user-images.githubusercontent.com/119410034/220532022-8201a2f9-ec32-4a94-8eef-4092ab313d88.png
https://user-images.githubusercontent.com/119410034/220532028-bd82a558-ce59-4872-9c47-feb49733122c.png
https://user-images.githubusercontent.com/119410034/220532032-e505e85f-2e38-49e4-a859-de0ed6923ff2.png

Lab_1 : run OpenSTA

Following files shows the steps to read all the above inputs & perform the timing check


https://user-images.githubusercontent.com/119410034/220537196-a31d3d7b-faae-45b2-beeb-92f82d526227.png

Following the command use to run OpenSTA

sta run.tcl -exit | tee run1.log

After the execution of above command , all inputs are being read as show in below image :-


https://user-images.githubusercontent.com/119410034/220533008-e0aa7e9e-0f19-4cb4-abbe-bfba8c1847de.png

Reports the Timing results in below image

https://user-images.githubusercontent.com/119410034/220533123-2bf0acd0-c1fb-405e-bf06-95d2f280c2e5.png




Day2
Lab_2 : Liberty Files

The .lib file is an ASCII representation of the timing & power parameters associated with any cell in a particular semiconductor technology

It contains the information like :- -I/O delay paths -Timing check values -Interconnect delays

Following the command to read liberty file in OpenSTA :-

read_liberty 

Lab_2 : Exercise 1

"Find all cells in simple_max.lib" Total 211 cells are present 


https://user-images.githubusercontent.com/119410034/220534292-c36e3268-ee74-4908-ad9b-e317e8104d63.png


"Find all pins of NAND2_X1" All pins w.r.t NAND2_X1 & their direction can be found from lib file as shown below :- 


https://user-images.githubusercontent.com/119410034/220534588-7cbfe431-da94-4a52-81a4-fbc156f25088.png
https://user-images.githubusercontent.com/119410034/220534600-c896855a-6774-4950-9906-6e0667736d8e.png

"Find Different between NAND2_x1 & NAND3_X1" Difference between NAND2_x1 & NAND3_X1 is highlighted in below image :-

https://user-images.githubusercontent.com/119410034/220534952-d59b07cf-e07d-4e11-9aa3-7c62fb458786.png

Lab_2 : Exercise 2

https://user-images.githubusercontent.com/119410034/220535114-c81e69e4-1e8c-4ec1-9118-3d3030d75275.png




Day3
Lab_3 : Understanding Slack Compulation

Following the circuit provided to perform the slack compulation calculation


https://user-images.githubusercontent.com/119410034/220535317-c3f0f017-c7ef-4d39-9896-81480364540a.png

Following snap shows the command & inputs used for slack computation :- report_checks -from F1/CK


https://user-images.githubusercontent.com/119410034/220536141-9423a2be-255d-4317-b4db-4af66b4edc5c.png

This will report slack compulation w.r.t that path as shown in below image :-


https://user-images.githubusercontent.com/119410034/220536238-ebe73723-43c2-4b84-bd30-3fdf23744b6d.png

report_checks -from F1/CK -endpoint_count 100


https://user-images.githubusercontent.com/119410034/220536354-83dbdf3f-a4d3-4b01-ac4b-822cbc566dbf.png




Day4
Lab_4 : Clock Gating Check


https://user-images.githubusercontent.com/119410034/220536692-0d64dab1-9dd7-4cab-b572-bf85203c479d.png

https://user-images.githubusercontent.com/119410034/220536760-f34527a0-d345-44dd-ba27-6629e5ab2a0c.png


Lab 4 : Async Pin Check


https://user-images.githubusercontent.com/119410034/220536827-9c5d1b26-de27-4e5c-a457-3f2e228429ee.png


