# Simplified-SLEX-Southwoods-Toll-Matrix-System
Introduction to HDL Laboratory (LBYCPF2) course using the VHDL programming language in the Vivado software.

## Introduction
The South Luzon Expressway, formally known as SLEX, is one of the most widely used 
limited-access expressways in Luzon, connecting Metro Manila to nearly all the major provinces 
of CALABARZON. It is a four-lane toll road spanning nearly 50 kilometers in length from start 
to end. The toll gates it features serve to recoup the costs of construction and maintenance, as well 
as to provide the funds needed for implementing further improvements later on. The Philippines 
has recently started its gradual shift to RFID payment systems in toll gates nationwide; phasing 
out the previous system of using cash. This saves significant amounts of time for each individual 
transaction as each vehicle would have an RFID sticker that will only be scanned by the toll gate 
and deduct the required payment from the driver’s balance, reducing the factors that lead to traffic 
jams in high-density areas. In places like expressways where faster travel times are the status quo, 
holdups due to traffic congestion are outright unacceptable given the payment that its drivers will 
be providing to access it in the first place.<br/><br/>
The recreation of this system delved on a single toll gate matrix based on the current rates 
stated in the toll regulatory board of the Department of Transportation website. As there are 
multiple entry/exit locations that can be chosen, the project only focuses on one of these with 5 
exit/entry locations for each vehicle class, resulting in a circuit that can have up to 15 possible toll 
rates. The Southwoods entry/exit toll location was chosen to include the scenario of different tolls 
requiring the same amount of payment in creating the circuit’s source code. This reconstruction in 
the form of a Verilog digital circuit aims to break down the fundamental operations and conditions 
that exist in the typical processes of a typical toll gate using concepts and coding conventions 
gained from the course throughout the academic year

## Source Codes Explanation
The toll system source codes feature a total of three inputs, namely a 2-bit input to identify 
vehicle class, a 3-bit input to identify its entry/exit location, and a 10-bit input that holds each 
vehicle’s RFID balance. The input port class pertains to the three vehicle classifications in the 
Philippines as identified by local toll matrix systems. Class 1 vehicles include private cars, 
jeepneys, vans, pick-ups, and motorcycles. Class 2 vehicles are buses, trucks, and class 1 vehicles 
attached with a trailer. Class 3 vehicles consist of large trucks like those that are used for delivering 
products and raw materials to factories in large quantities. They are classified according to their 
height and the number of their axles. The input port loc (or location) dictates the origin point from 
where the vehicle came from in passing through the chosen entry or exit point, Southwoods. From 
the 10 possible locations that the SLEX Southwoods toll matrix can charge for, only five were 
chosen in creating this simplified version of the toll matrix. These locations were used as 
parameters and assigned specific binary value identifiers as seen in line 29. Location or parameter 
SKY refers to Skyway, MAG for Magnolia, C5 as C-5, BIC for Bicutan, and SUC for Sucat. Each 
location or source point has different set rates based on the actual values found in the Toll 
Regulatory Board website where the actual SLEX toll matrix rates per vehicle class can be found. 
The 10-bit input load is the variable that holds the payment from each individual driver. 
Correspondingly, the 10-bit output change and 1-bit output out are the possible outputs of the toll 
system. The 10-bit change caters to the 10-bit load that could reach a certain high, but realistic 
amount of cash. The 1-bit output only has a value of logic high or logic low. An output of logic 
high means that the driver has sufficient cash to pay the toll fee, and that the toll gate has detected 
a valid vehicle number and location in its inputs. Conversely, a logic low depicts anything 
otherwise.<br/><br/>
The code is set in a way that there will only be a change in the outputs whenever the system 
detects changes in any of the three inputs. These are the parameters within the always block that 
would trigger the circuit within that block to execute. The module begins with an if statement that 
checks for the value of the class. It is followed by another if statement that checks for the value of 
the loc. The next if statement checks if the input load is greater than or equal to a specific value. 
The specific values used throughout the program are the binary equivalents of the toll fee to be 
paid. The input change is the difference between the load and the amount of the toll fee, and the 
output out results to a 1 if having a value for the change is applicable, and 0 if the input load of 
cash from the driver is not enough to pay for the toll fee. The output change in the else statement 
of the innermost if-else block results in an X if it is impossible to have a value for the output 
change. In line 110, as the program only limits to having five locations, the else statement which 
may be coming from other possible combinations for the other possible locations results in a value 
of X in both output change and output out. This pattern is seen throughout the whole program. The 
only difference is that classes 2 and 3 utilize the case statement with parameter loc instead of nested 
if statements in class 1. The nested if statements and the case statements mean the same thing, just 
with a different implementation. With this having said, advancing in line 289, as there are only 
three classes, other possible inputs for that variable is impossible, and so output change and output 
out will have a value of X. The approach of the source codes first checks for the value of the class 
then checks the location where the vehicle is coming from, then checks for the value of the input 
load if it is sufficient or not to pass through the toll gate which determines the values for output 
change and output out. The tables above are the toll fee basis for each input loc (or source point), 
and vehicle classifications, entering or exiting Southwoods.

## Analysis and Conclusion
For the waveform simulations, each class has two screenshots each, following a certain, 
specific format. This means that for every two screenshots from Figures 1a to 3b, the value of the 
input class is constant. Each simulation cycle is marked with a blue marker, indicating the end and 
the start of another simulation. Figures 1a, 2a, and 3a have a total of six simulations, whereas 
figures 1b, 2b, and 3b have a total of five simulations. Each simulation cycle also differs in its 
input loc. The first half of each of the simulation cycles of Figures 1a, 2a, and 3a first checks if 
output change will have a value of 1 (as the input load is the sum of the toll fee plus 1), and if 
output out is logically high. The second half has an input load of 001 (technically 1), and checks 
if output change will result in series of X’s, and output out is logically low. The last simulation 
cycle of these figures has an input loc that isn’t considered in the source codes, and it resulted in 
an output change and output out of an X. Figures 2a, 2b, and 2c follow the same format as the 
other figures, but now check if output change will have a value of 200 in the first half, and 400 in 
the second half of each simulation cycle. The input load is systematically assigned once again, 
with its values being the sum of the toll fee and PHP 200 in the first half of each simulation cycle, 
and the sum of the toll fee and PHP 400 in the second half. It is observed that in all figures, their 
outputs worked as expected. Having a value in the output change will also produce a logically high 
output for output out. This means that the driver can pass through the toll gate. No value in the 
change or an output of X will produce a logically low output for output out, and this means that 
the driver has insufficient load or cash to pay for the toll gate. <br/><br/>
The implementation of a Verilog code to a toll system is possible through different 
simulations, analyses, and syntheses. The Xilinx software provides circuit synthesis and the 
Verilog language models electronic systems. As the project title suggests, Simplified SLEX 
(Southwoods) Toll Matrix System, used the SLEX toll system as a reference but only selected one 
entry or exit point, and only five of the possible source points. By setting inputs for the classes, 
source points, and payments, the circuit provided outputs for the change and the state of being 
allowable to pass through the toll gate. The project’s source codes utilized Verilog’s reserve words 
such as always, input, output, reg, parameter, begin, end, case, endcase, if, else, and endmodule. 
Therefore, since the source codes compose of the keywords always, if, else if, else, begin, end, 
case, and endcase, it is composed of sequential statements with a blocking assignment. In addition, 
the project made use of Verilog’s arithmetic operators and relational operators. The use of Verilog 
has its practical, evident, real-world applications in designing circuit systems, and is further proved 
by the usage of the language in this project.

### Authors

#### Arciella Brience C. Crisostomo [arciella_brience_crisostomo@dlsu.edu.ph]

#### Dustin Kyle D. Landicho [dustin_kyle_landicho@dlsu.edu.ph]
