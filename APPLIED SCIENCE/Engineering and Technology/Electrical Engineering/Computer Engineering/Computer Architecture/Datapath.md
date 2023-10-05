A datapath is a computer circuit that can be pipelined. It usually consists of multiple individual portions that can be broken down. For the purposes of this note, we refer to datapath designs in the traditional sense (as they refer to general processors).

## Evolution

The Von Neumann implementation of a pipelined processor evolved in the following order:

1. [[Sequential processors]] (SPs) held direct implementations of sequential execution. These were poor for performance.
2. [[Pipelined processors]] (PPs) overlapped execution of multiple instructions. An example is the [[MIPS Five Stage Datapath]].
3. [[Super-scalar processors]] (SSPs) handled out-of-order execution of multiple instructions.
4. [[Multi-core processors]] (MCPs) handled multiple concurrent threads, or programs.
5. Finally, [[heterogeneous multi-processors]] (HMPs) handle multiple concurrent tasks on diverse co-processors. They break up computations and split them across individual specialized cores.

## Construction

A datapath consists of many individual components which are necessary for computation. As noted in [[Pipelining (Computation)#Stages|pipeline stages]], these designs can be split across many individual stages. However, the datapath tends to have the following parts:

- An [[Read-Only Memory (ROM)|instruction memory]];
- A [[control unit]];
- A set of [[Register Memory|registers]];
- Some [[Memory (Computing)|data memory]];
- An [[Arithmetic Logic Unit (ALU)]], primarily utilized for processing.

Other complicated datapaths may contain other components. Non-traditional datapaths may also forego these individual components in favor of more problem-specific solutions.