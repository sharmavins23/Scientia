Pipelining is the procedure of taking chunks of an individual computer [[Pipelining (Computation)#Datapath|datapath]] and parallelizing them. In doing so a computer can (for the cost of small start-up latency) perform instructions much faster.

## Datapath

A datapath is a computer circuit that can be pipelined. It usually consists of multiple individual portions that can be broken down. For the purposes of this note, we'll refer to a datapath in the processing sense.

### Evolution

The Von Neumann implementation of a pipelined processor evolved in the following order:

1. [[Sequential processors]] (SPs) held direct implementations of sequential execution. These were poor for performance.
2. [[Pipelined processors]] (PPs) overlapped execution of multiple instructions. An example is the [[MIPS Five Stage Datapath]].
3. [[Super-scalar processors]] (SSPs) handled out-of-order execution of multiple instructions.
4. [[Multi-core processors]] (MCPs) handled multiple concurrent threads, or programs.
5. Finally, [[heterogeneous multi-processors]] (HMPs) handle multiple concurrent tasks on diverse co-processors. They break up computations and split them across individual specialized cores.

## Mathematical Modelling

Suppose we define a computer architecture with a bandwidth $B$ corresponding to the number of tasks per unit time. For a system that performs one task at a time, the bandwidth can be computed as:

$$B=\frac{1}{t_{del}}$$

In this equation, $t_{del}$ is the time delayed per executed process (or the total time it took to *compute* a process).

Naively, if $t_{del}$ can be split into discrete 'chunks' which can be parallelized, we can increase bandwidth correspondingly. As such, our bandwidth can simply 'scale' up with pipeline depth, or the number of stages our pipeline has.

We can concretize this model. Let's define $k$ as the number of stages, or a value of our pipeline depth, and $t_{pd}$ as a propagation delay for a particular stage (which is a constant, and for our purposes, cannot be reduced further). We'll add an extra delay $t_L$ through a latch, which will synchronize stages. As such, the processor's performance $P$ may be:

$$P=B=\frac{1}{\frac{t_{pd}}{k} + t_L}$$

Naively, by increasing the number of stages $k$, we can also increase throughput. The cost $C$ of the design will also scale from the initial cost $C_0$ and the cost of adding other latches $C_L$ as:

$$C=kC_L + C_0$$

We can create a cost/performance trade-off which is relatively easy to compute. As we change $k$, we want to find some stability point:

$$\frac{\partial}{\partial k}\left(\frac{kC_L + C_0}{\frac{1}{\frac{t_{pd}}{k} + t_L}}\right)=\frac{\partial}{\partial k}\left(t_{pd}C_L + kC_Lt_L + \frac{C_0t_{pd}}{k} + C_0t_L\right)$$

Computing this derivative:

$$
=0 + C_Lt_L - \frac{C_0t_{pd}}{k^2} + 0=C_Lt_L - \frac{C_0t_{pd}}{k^2}
$$

We can further solve for $k$ to get an optimal number of pipeline stages.

$$
k_{opt}=\sqrt{\frac{C_0t_{pd}}{C_Lt_L}}
$$

By simply plugging in variables, we can compute optimal pipeline depths. However, this model makes some key assumptions:

- Pipeline stages are uniform in timing, which (in practice) they seldom are;
- Identical computations will be done, which they seldom are;
- All computations are mutually independent, which they seldom are.

## Stages

Pipeline stages may be chosen in order to speed up a processor. Multiple sub-computations can be merged into a single stage, or a computation can be divided into multiple sub-computations. Recent trends have been focusing on generating deeper pipelines with higher clock speeds per stage.

The following are a series of common and canonical stages for pipelined processors.

### Instruction Fetch (IF)

Fetching generally involves pulling instructions from [[ROM]]. Usually, programs are stored in ROM for security reasons (as programs should ideally not be modified by other programs!) Any [[control flow]] changes may occur within this stage as well.

The ROM data can be sequentially read out, or (in the case of a jump), some other address may be specified to pull from.

### Instruction Decode (ID)

This stage involves decoding the instruction from its smaller binary format into commands that the entire [[Pipelining (Computation)#Datapath|datapath]] may utilize. Usually, this involves some form of control unit managing the function of the entire datapath.

#### Operand Fetching (OF)

This stage is often merged into [[Pipelining (Computation)#Instruction Decode (ID)|Instruction Decode]]. Within this, operands for computations are fetched either from memory or from registers. This is often relatively trivial for some [[Instruction Set Architecture|ISAs]] as they only utilize register-register operations (such as in [[MIPS Architecture|MIPS]]).

### Execution (EXE)

This stage contains the 'bread and butter' of a computer, sporting an [[arithmetic logic unit|ALU]] which performs instructions.

### Memory Access (MEM)

This stage is usually the longest stage of a pipeline, as it incurs the cost of going to memory and interfacing with the [[Memory|memory]] hierarchy.

#### Operand Store (OS)

This stage is often merged into [[Pipelining (Computation)#Memory Access (MEM)|Memory Access]] (for the same trivial reason as in [[Pipelining (Computation)#Operand Fetching (OF)|Operand Fetching]]). Within the stage, operands are stored into their output locations.

### Write-Back (WB)

This stage is often called "PC", or Program Counter, as it refers to updating the [[register|registers]] (including the Program Counter register, or the register responsible for keeping track of position in the execution).

## Hazards

When executing instructions in parallel, one particular issue arises with data that is computed later in the pipeline than it is accessed. There are a series of important dependency hazards that might produce incorrect execution unless otherwise handled:

- Read-after-Write (RAW) hazards occur when data needs to be read immediately after an instruction writes it. This is a 'true' dependency hazard, as it tends to stall out pipelines significantly. These are also called data dependencies.
- Write-after-Read (WAR) hazards are where data is written after it is read. Since the data is already previously fetched, this dependency doesn't need to be handled. It is called an anti-dependency.
- Write-after-Write (WAW) hazards are also called 'false' dependency hazards. Since the act of writing does not depend on what is previously in the register, this dependency does not matter.
- Control hazards are hazards that arise due to changing of control-flow instructions. Since control flow changes, anything queued in the pipeline needs to not execute.

Other problems exist within the [[datapath]], such as arithmetic overflow, invalid instructions, illegal memory accesses, and divide-by-zero errors. These are usually called [[Exceptions|exceptions]].