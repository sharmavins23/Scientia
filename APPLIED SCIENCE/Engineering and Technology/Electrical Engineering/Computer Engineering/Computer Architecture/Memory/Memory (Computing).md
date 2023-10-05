Computer memory refers to particular circuits that store data.

## Types

There are several ways of categorizing memory. One of the popular ones is by reading speed and efficiency:

1. [[Read-Only Memory (ROM)]];
2. [[Hard Disk Memory]];
3. [[Solid-State Memory]];
4. [[Random Access Memory (RAM)]];
5. [[Cache Memory]];
6. [[Register Memory]].

These are also ordered based on decreasing proximity to the CPU [[Datapath|datapath]] as well, and are also ordered in terms of increasing cost to increase.

## Buffers

Buffers are a method for implementing memory. There are four popular ways to implement buffers:

1. With indexed memory, a $k$-bit index is fed into a decoder. This allows for $2^k$ memory blocks.
2. Fully associative memory (or content-addressable memory) uses a $k$-bit key, but each memory block has a $k$-bit tag. The tags are checked on each memory block, so this structure is faster.
3. $n$-way set-associative memory uses a $k$-bit index, as well as $2^k \times N$ blocks. The index is used to decode into a particular fully associative memory block, where a tag is then matched.
4. Multi-ported memory may finally have multiple indices that can be used in parallel to access the memory. The easiest implementation of this simply duplicates the memory for other ports.

## Volatility

Some circuit designs for memory discharge slowly over time and over use, and others discharge when read. Memory that needs to be recharged is called 'volatile' memory, as it will reset when power is lost. Memory that does not need to be recharged and can last for longer periods of time is called non-volatile memory or non-volatile storage.