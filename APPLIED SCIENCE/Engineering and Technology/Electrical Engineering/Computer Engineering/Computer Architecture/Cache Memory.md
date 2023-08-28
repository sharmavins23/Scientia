Cache memory is specialized memory designed solely for [[speedup]]. Instead of paying the latency penalty of looking in slower memory every time, a computer may store recent results of memory lookups in cache and retrieve them from this super-fast memory instead.

## Hierarchy

Caches often have hierarchies, with smaller cache blocks placed closer to the CPU. This comes with particular throughput and latency tradeoffs.

In CPUs, cache memory is split into levels:

1. L1 cache is generally per-core, and each individual core may read from this cache.
2. L2 cache is sometimes per-core, or sometimes shared between cores.
3. L3 cache is usually shared between cores.

L1 memory is smaller than L2, but faster (due to proximity).