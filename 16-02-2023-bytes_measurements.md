```
Byte Values (2 potency)
-----------
Kilobyte  | 1024 KB => max: 2^10 (1,024)
Megabyte  | 1024 MB => max: 2^20 (1,048,576)
Gigabyte  | 1024 GB => max: 2^30 (1,073,741,824)
Terabyte  | 1024 TB => max: 2^40 (1,099,511,627,776)
Petabyte  | 1024 PB => max: 2^50 (1,125,899,906,842,624)
Exabyte   | 1024 EB => max: 2^60 (1,152,921,504,606,846,976)
Zettabyte | 1024 ZB => max: 2^70 (1,180,591,620,717,411,303,424)
Yottabyte | 1024 YB => max: 2^80 (1,208,925,819,614,629,174,706,176)
```

```
Latency Comparison Numbers
--------------------------
L1 cache reference                           0.5 ns
Branch mispredict                            5   ns
L2 cache reference                           7   ns                      14x L1 cache
Mutex lock/unlock                           25   ns
Main memory reference                      100   ns                      20x L2 cache, 200x L1 cache
Compress 1K bytes with Zippy            10,000   ns       10 us
Send 1 KB bytes over 1 Gbps network     10,000   ns       10 us
Read 4 KB randomly from SSD*           150,000   ns      150 us          ~1GB/sec SSD
Read 1 MB sequentially from memory     250,000   ns      250 us
Round trip within same datacenter      500,000   ns      500 us
Read 1 MB sequentially from SSD*     1,000,000   ns    1,000 us    1 ms  ~1GB/sec SSD, 4X memory
HDD seek                            10,000,000   ns   10,000 us   10 ms  20x datacenter roundtrip
Read 1 MB sequentially from 1 Gbps  10,000,000   ns   10,000 us   10 ms  40x memory, 10X SSD
Read 1 MB sequentially from HDD     30,000,000   ns   30,000 us   30 ms 120x memory, 30X SSD
Send packet CA->Netherlands->CA    150,000,000   ns  150,000 us  150 ms

Notes
-----
1 ns = 10^-9 seconds
1 us = 10^-6 seconds = 1,000 ns
1 ms = 10^-3 seconds = 1,000 us = 1,000,000 ns
```
