# WildRig Multi
multi algo miner for AMD & NVIDIA

# KNOWN ISSUES
- rejected shares on Vega gpu's for progpow family of algorithms if use kernel 2(kernel 1 works fine)
- broken mtp algorithm under Linux, miner can't find any share
- not all algorithms working on NVIDIA gpu's right now, and not all of them are optimized(see Release Notes)
- broken honeycomb algoithm, last working version is **0.17.6**
- "Duplicate share" error on some pools for progpowz
- any report is welcome! :)

# SUPPORTED GPU's
## AMD:
- **GCN 2nd gen**: R7 260, R9 290, R9 295X2, R7 360, R9 390
- **GCN 3rd gen**: R9 285, R9 380, R9 Fury, R9 Nano
- **GCN 4th gen**: RX460, RX470, RX480, RX550, RX560, RX570, RX580, RX590
- **GCN 5th gen**: Vega 11, Vega 56, Vega 64, Radeon VII
- **RDNA 1st gen**: Radeon 5500XT, Radeon 5600XT, Radeon 5700, Radeon 5700XT
- **RDNA 2nd gen**: Radeon 6500XT, Radeon 6600XT, Radeon 6700 XT, Radeon 6800XT, Radeon 6900 XT

## NVIDIA:
- All gpu's with Compute Capabilities >=5.0 should work
- also specific gpu can be supported via use of --ptx-version parameter(like --ptx-version 71 for sm_86, more ptx version is [here](https://docs.nvidia.com/cuda/parallel-thread-execution/#release-notes))

# SUPPORTED ALGORITHMS
- aergo, anime
- bcd, bitcore, blake2b-btcc, blake2b-glt, blake2s, bmw512
- c11
- dedal
- exosis
- geek, ghostrider, glt-astralhash, glt-globalhash, glt-jeonghash, glt-padihash, glt-pawelhash
- hex, hmq1725, honeycomb
- kawpow
- lyra2tdc, lyra2v2, lyra2v3, lyra2vc0ban
- megabtx, megamec, minotaur, mtp, mtp-tcr
- nist5
- phi, phi5, polytimos, progpowz, progpow-ethercore, progpow-sero, progpow-veil
- quark, quibit
- renesis
- sha256, sha256csm, sha256d, sha256q, sha256t, skein2, skunkhash, sonoa
- timetravel, tribus
- vprogpow
- wildkeccak
- x11, x11k, x12, x13, x14, x15, x16r, x16rv2, x16s, x17, x17,r x18, x20r, x21s, x22i, x25x, x33, xevan
