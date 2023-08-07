A CPU core is an individual [[Datapath|datapath]] designed for the handling of general-purpose instructions.

## L1 Cache

Most processor cores contain an individual [[Cache Memory|cache]] within the CPU core. This cache is extremely small, but due to its extreme proximity, is therefore extremely fast and efficient.

## Threads

The CPU datapath may be designed such that it can handle multiple instructions at once (in something known as [[Super-scalar processors|super-scalar processor design]]). These are the individual "threads" of computation - They are capable of handling multiple logical threads.

As thread count is inherently derived from the architecture itself, increasing thread count per core comes with significant cost and complexity increases, as dependency issues become more prevalent.

Generally, thread count is listed as an absolute value alongside core count, rather than a per-core value. With a processor that has 2 cores and 4 threads, a total of 4 individual 'lines of instruction' (threads) can be run in parallel *if* they have no interlocking dependencies. Each core (datapath design) may process two threads simultaneously.