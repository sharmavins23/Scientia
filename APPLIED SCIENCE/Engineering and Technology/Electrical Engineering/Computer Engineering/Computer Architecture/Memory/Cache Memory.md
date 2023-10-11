Cache memory is specialized memory designed solely for [[speedup]]. Instead of paying the latency penalty of looking in slower memory every time, a computer may store recent results of memory lookups in cache and retrieve them from this super-fast memory instead.

## Hierarchy

Caches often have hierarchies, with smaller cache blocks placed closer to the CPU. This comes with particular throughput and latency tradeoffs.

In CPUs, cache memory is split into levels:

1. L1 cache is generally per-core, and each individual core may read from this cache.
2. L2 cache is sometimes per-core, or sometimes shared between cores.
3. L3 cache is usually shared between cores.

L1 memory is smaller than L2, but faster (due to proximity).

## Sizing

Cache blocks are usually defined in an $(S, E, B)$ triplet. In this structure, the cache's total size is $S\times E\times B$.

The $E$ refers to the $2^e$ number of cache lines per set, where each cache 'line' consists of a valid bit, a tag, and $2^b$ bytes per cache block. There are $2^s$ sets. Note that an $n$-way associative cache does not have $n$ sets.

Different values of $E$ are also called different 'ways' for a cache. For instance, $E=1$ is a directly mapped cache; $E=2$ is a two-way set associative cache.

A word has an address of $(t, s, b)$. For a cache with 4 bytes per block, the block offset $b$ must have $2$ bits (to index all $4$ bytes). Similarly, if there are two cache lines, the $s$ value must be $1$.

## Misses

Since a cache has fixed sizing, it is (necessarily) prone to 'miss' address lookups. In this case, the computer must instead go to the memory system and fetch data.

There are three types of misses:

- Cold misses occur when a cache has never experienced a tag within the cache/set. These are also called compulsory misses.
- Capacity misses occur when a particular tag's working set (the number of unique tags added to the set in between the last same tag) is greater than or equal to the size of the set. These misses can be solved by increasing the size of the cache.
- Conflict misses refer to misses that *could* be solved by re-arranging the cache. These misses are due to the scheduling policy and memory organization, not the capacity of the system.

Cache miss rate can be computed easily. For a cache, the miss rate is generally based on block size - A first fetch will cold miss, and subsequent fetches may or may not miss. For instance, if a cache has 16 byte blocks and we fetch 4 byte words in a loop, our cache miss rate will be 25%, as we cold miss, then fetch three correctly, then miss.