
# Day 1 :

# Lab_1 : About OpenSTA
OpenSTA is a gate level static timing verifier. As a stand-alone executable it can be used to verify the timing of a design using standard file formats like :-

-Verilog netlist
-Liberty library
-SDC timing constraints
-SDF delay annotation
-SPEF parasitics

OpenSTA is architected to be easily bolted on to other tools as a timing engine.

By using a network adapter, OpenSTAcan access the host netlist data structures without duplicating them.

Query based incremental update of delays, arrival and required times & Simulator to propagate constants from constraints and netlist tie high/low

OpenSTA pdf :


![OpenSTA](./OpenSTA_pdf/OpenSTA.pdf)

# Lab_1 : Inputs to OpenSTA
```
cd lab1
simple.v
```
![day1](./images/day1_1.png)


Liberty File : Standards Cells Information is present in `liberty` or `.lib` file
.lib life


![day1](./images/day1_2.png)
![day1](./images/day1_3.png)
![day1](./images/day1_4.png)




# Lab_1 : run OpenSTA

Following files shows the steps to read all the above inputs & perform the timing check


![day1](./images/day1_5.png)

Following the command use to run OpenSTA

```
sta run.tcl -exit | tee run1.log
```

After the execution of above command , all inputs are being read as show in below image :-


![day1](./images/day1_6.png)

Reports the Timing results in below image

![day1](./images/day1_7.png)




# Day2 : 


# Lab_2 : Liberty Files

The .lib file is an ASCII representation of the timing & power parameters associated with any cell in a particular semiconductor technology

It contains the information like :- -I/O delay paths -Timing check values -Interconnect delays

Following the command to read liberty file in OpenSTA :-

`read_liberty`

Liberty file will following information 
![liberty1](./images/libert1.png)
![liberty2](./images/libert2.png)
![liberty3](./images/liberty3.png)

# Lab_2 : Exercise 1

Find all cells in "simple_max.lib" Total 211 cells are present 


![day2](./images/day2_1.png)


Find all pins of 'NAND2_X1' All pins w.r.t 'NAND2_X1' & their direction can be found from lib file as shown below :- 


![day2](./images/day2_2.png)


![day2](./images/day2_3.png)


Find Different between "NAND2_x1 & NAND3_X1" Difference between NAND2_x1 & NAND3_X1 is highlighted in below image :-

![day2](./images/day2_4.png)


# Lab_2 : Exercise 2
Understand the report

![day2](./images/day2_5.png)


# Day3 :


# Lab_3 : Understanding Slack Compulation

Following the circuit provided to perform the slack compulation calculation


![day3](./images/day3_1.png)


Following snap shows the command & inputs used for slack computation :-
```
report_checks -from F1/CK
```

![day3](./images/day3_2.png)


This will report slack compulation w.r.t that path as shown in below image :-


![day3](./images/day3_3.png)

```
report_checks -from F1/CK -endpoint_count 100
```

![day3](./images/day3_4.png)





# Day4 :


# Lab_4 : Clock Gating Check
% cat s27.v

![day4](./images/day4_1.png)
```
cd lab6
leafpad run.tcl
sta run.tcl ???exit | tee run.log
```

![day4](./images/day4_2.png)



# Lab 4 : Async Pin Check
```
cd lab7
leafpad run.tcl
sta run.tcl ???exit | tee run.log
```
![day4](./images/day4_3.png)



# Day5 :


# Lab_5 :slack computation


![day5](./images/day5_1.png)


From the above figure we have to analyze the path in the report of the slack
```
cd lab3
sta run.tcl -noexit | tee out.txt
```

![day5](./images/day5_2.png)



# Exercise 
Analyze each path in detail and understand
```
report_checks ???from F1/CK -endpoint_count 100
```
![exe](./images/exe1.png)



Commom path pesimism removal('CPPR')
```
cd lab4
sta run.tcl ???exit | out.txt
report_checks ???to F2/D
```
![exe](./images/exe2.png)



With set sta_crpr_enabled 1 : 
```
set sta_crpr_enabled 1
report_checks -to F2/D
```
![exe](./images/exe3.png)



# ECO insertion
```
cd lab5
run.tcl
sta run.tcl ???exit | tee run.log'
```
![eco](./images/eco_insert.png)


Diff between s27.v and s27_eco.v

![diff](./images/gvimdiff.png)



Path for labs is ![here](https://github.com/vikkisachdeva/openSTA_sta_workshop/tree/master/vlsideepdive_openSTA_labs)


