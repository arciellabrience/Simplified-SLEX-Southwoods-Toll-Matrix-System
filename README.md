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
