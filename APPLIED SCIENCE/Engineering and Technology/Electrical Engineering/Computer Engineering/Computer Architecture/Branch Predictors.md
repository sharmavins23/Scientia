Branch predictors are an important facet of the [[Pipelining (Computation)#Instruction Fetch (IF)|instruction fetch]] stage of a datapath, and are the processing element responsible for [[speculative processing]] of instructions. They predict, for a given branching instruction, whether the branch is taken or not.

## Canonical Predictors

### Static Predictors

Static predictors differ from other canonical branch prediction techniques in that they simply do not take in runtime information and instead predict based on predetermined information. An example of this is the `NeverTakenBP`, a branch predictor that simply predicts the branch is not taken.

### 2-bit Saturating Counter

A 2-bit saturating counter is a finite state machine approaching near maximal efficiency with four simple states (and two bits). Professor Smith has his own design; The up-down saturating counter is more popular.

### Two-level Adaptive Branch Predictors

In the context of a singular branch instruction, often taken/not taken history of that branch (local history) is not enough information. The path taken may influence the instruction's performance; As such, path history (global history) may help.

#### `GlobalHistBP`

The most common of these is a `GlobalHistBP`, or a global history branch predictor. This predictor has a global history register (GHR), which is effectively a FIFO queue of bits referring to the previous global taken-ness (`1` is taken, `0` is not taken). The BHR value is used to index into a pattern history table (PHT), and each PHT entry is its own 2-bit saturating counter.

A popular iteration of this is `GShare`, which XORs the BHR with the branch address, thus better distributing items across the table.

#### `LocalHistBP`

Local history branch predictors use some portion of the branch address in order to index into the branch history table (BHT), which is simply a list of BHRs.

#### Two-level Adaptive

The PC can also be used to index into a two-dimensional pattern history table (PHT). This offers even more control as well. The first level is the branch history registers, and they can be referred to as 'GA' if globally adaptive (one BHR) or 'PA' if per-address adaptive (multiple BHRs in a BHT).

The second level is a set of pattern history tables. The predictor is referred to as 'g' if only one PHT exists; 's' if a shared table exists but is redundant, or if some arbitrary hashing function is used for PHT addressing; and 'p' if it's indexed as well by branch address.

The `GlobalHistBP` is a GAg predictor. The `LocalHistBP` is a PAg predictor. PAp predictors are also extremely popular.

### Bi-mode Predictor

A bi-mode predictor is constructed as a GAp predictor, where the prediction from the PHT is chosen based on another 'choice predictor' PHT. The choice predictor is indexed via the branch address.

Bi-modal predictors aim to separate PHTs for biased branches.

### G-Skewed Predictor

G-skewed predictors manipulate multiple hashing functions (instead of just g-share) to index into multiple PHTs, and use a majority vote at the end.

### Agree Predictor

An agree predictor uses a BTB to get a basic prediction, with a PHT denoting whether the BTB should be agreed with or not.

### YAGS

Yet Another Global Scheme is a predictor structure that uses small caches instead of PHT tables. Otherwise, biased taken/not taken paths are structured similarly to a bi-modal predictor.

### Perceptron Predictor

The perceptron predictor is based on the original design of the [[Neuron (Computer Science)|neuron]], or the [[Perceptron|perceptron]]. This AI concept was adapted for branch prediction and quickly became a strong branch predictor due to its learning functionality and capability.

### Tournament Predictor

Tournament predictors are often 'composed' predictors, and are combined of other predictors with a voting scheme to handle choosing between their outputs.

The Alpha 21264 PC utilized a tournament meta-predictor composed of a GShare predictor and a PAp predictor.

### TAGE Predictor

The TAGE predictor was a winner of branch prediction competitions, and used its own waterfall flowing design and tag system in order to function properly.