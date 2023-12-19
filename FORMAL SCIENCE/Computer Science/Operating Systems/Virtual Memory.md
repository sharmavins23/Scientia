Virtual [[Memory (Computing)|memory]] addresses are utilized for security purposes in [[Operating System|OS]] design, and effectively 'mask' the underlying physical hardware. The translation is relatively similar, and is similar in construction to [[Cache Memory|cache addressing]].

Virtual memory sizings do not have to correlate to physical address size. Oftentimes, virtual address spaces are much smaller - They can also be larger.

## Worked Example

Suppose we have a design with a virtual address of 18 bits, a physical address of 12 bits, a page size of 512 bytes, an 8-way set associative TLB (with 2 indices), and a 2-way set associative cache (with 4 indices, and 4 byte blocks).

First, the virtual page offset (VPO) is computed - This is the location in the page. For an example page size of 512 bytes, we need 9 bits here. Next, the virtual page number can be everything else. If we have an 18-bit virtual address, we can have a total of 512 pages in total.

The TLB index is part of the VPN. This effectively tells the location in the TLB cache for a piece of memory. Since we have two indices for our TLB, we need only 1 bit. As such, the TLBI is the least significant bit in the VPN. The remainder of the VPN is the TLB tag.

Our address now looks like this:

| 17  | 16  | 15  | 14  | 13  | 12  | 11  | 10  | 9   | 8   | 7   | 6   | 5   | 4   | 3   | 2   | 1   | 0   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| VPN | VPN | VPN | VPN | VPN | VPN | VPN | VPN | VPN | VPO | VPO | VPO | VPO | VPO | VPO | VPO | VPO | VPO |
| TLT | TLT | TLT | TLT | TLT | TLT | TLT | TLT | TLI |     |     |     |     |     |     |     |     |     |

Our physical page address is also similar. The physical page offset, or PPO, is the same as the VPO, so 9 bits are required. The PPN is everything else (so, $12-9=3$ bits).

The cache offset (CO) is the offset in a block. Since there are four blocks, the least significant 2 bits of the page address is the CO. The cache index CI needs 2 bits for 4 indices, so the next 2 significant bits are our CI. The cache tag is everything else.

| 11  | 10  | 9   | 8   | 7   | 6   | 5   | 4   | 3   | 2   | 1   | 0   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| PPN | PPN | PPN | PPO | PPO | PPO | PPO | PPO | PPO | PPO | PPO | PPO |
| CT  | CT  | CT  | CT  | CT  | CT  | CT  | CT  | CI  | CI  | CO  | CO  |

### Translating Addresses

Let's translate `0x1A9F4`. On the bit representation, we get:

```
..01 1010 1001 1111 0100
```

The leading bits are truncated. As such, we can extract a few things:

- Our VPN is 9 bits, so `0 1101 0100` becomes `0x0D4`.
- Our VPO is 9 bits, so `1 1111 0100` becomes `0x1F4`. This is also our PPO.
- Our TLBI (or TLI) is 1 bit, so it's `0x0`.
- The remainder of our VPN is `0110 1010`, so our TLBT (or TLT) is simply `0x6A`.
- We can look in our TLB, and if index `0x0` has a value of `0x6A`, we can pull out the PPN and get a TLB hit (and no page fault!)
