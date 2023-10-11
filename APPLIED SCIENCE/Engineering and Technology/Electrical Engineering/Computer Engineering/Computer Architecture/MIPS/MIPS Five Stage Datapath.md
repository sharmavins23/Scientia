The MIPS Five Stage Datapath is an example processor design of a [[Von Neumann Architecture]] [[Pipelined processors|pipelined]] computer. An example of its design in Verilog can be found on [GitHub](https://github.com/sharmavins23/five-stage-datapath).

![[MIPS Five Stage Datapath.png]]

## Overview

The design is a 32-bit [[Pipelining (Computation)#Datapath|datapath]] designed to execute [[MIPS Architecture|MIPS assembly]] code. It also contains a [[Random-Access Memory (RAM)|RAM]] and [[Read-Only Memory (ROM)|ROM]] module, both of which are byte addressed. The original project runs on the Xilinx Zynq-7000 Programmable System on a Chip (package XC7Z010CLG400-1) [[field-programmable gate array]].

The functionality is split across five individual stages - [[Pipelining (Computation)#Instruction Fetch|Instruction Fetch]], [[Pipelining (Computation)#Instruction Decode|Instruction Decode]], [[Pipelining (Computation)#Execution|Execution]], [[Pipelining (Computation)#Memory Access|Memory Access]], and [[Pipelining (Computation)#Write-Back|Write-Back]]. These individual [[Pipelining (Computation)|pipeline]] stages execute one instruction per clock cycle each, and thanks to this pipelined design can execute up to five instructions concurrently.