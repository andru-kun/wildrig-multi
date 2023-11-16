# WildRig Multi
multi algo miner for AMD, NVIDIA and Intel gpu's

[Discord community](https://discord.gg/9pR7WMkt)

# KNOWN ISSUES
- **nexapow** is not supported on AMD gpu's with pre-RDNA architecture
- **x22i, x25x** is not suported on NVIDIA GPU's
- any report is welcome! :)

# SUPPORTED GPU's
## AMD:
- **GCN 2nd gen**: Radeon R7 260, R9 290, R9 295X2, R7 360, R9 390
- **GCN 3rd gen**: Radeon R9 285, R9 380, R9 Fury, R9 Nano
- **GCN 4th gen**: Radeon RX 460, 470, 480, 550, 560, 570, 580, 590
- **GCN 5th gen**: Radeon Vega 56, Vega 64, Vega FE, Radeon VII
- **RDNA 1st gen**: Radeon RX 5500XT, 5600XT, 5700, 5700XT
- **RDNA 2nd gen**: Radeon RX 6500XT, Radeon 6600XT, 6700 XT, 6750 XT, 6800XT, 6900 XT
- **RDNA 3nd gen**: Radeon RX 7700XT, 7800XT, 7900XTX/XT

Pitcairn, Tahiti and other old cards of **GCN 1st gen**(like HD 78x0, HD 79x0, R7 265, R9 270, R9 280, R9 370, etc.) are not supported and won't be, because they are too old and need additional work.

## NVIDIA:
- All gpu's with Compute Capabilities >=5.0 should work
- also specific gpu can be supported via use of --ptx-version parameter(like --ptx-version 71 for sm_86, more ptx version is [here](https://docs.nvidia.com/cuda/parallel-thread-execution/#release-notes))

## INTEL:
- **Intel Arc**: A310, A350M, A370M, A380, A530M, A550M, A570M, A580, A730M, A750, A770M, A770
- **Intel Arc Pro**: A30M, A40/A50, A60M, A60
- **Intel Data Center GPU**: Flex 140, Flex 170

# SUPPORTED ALGORITHMS
- aergo, anime
- bcd, bitcore, blake2b-btcc, blake2b-glt, blake2s, blake3, bmw512
- c11, curvehash
- dedal
- evrprogpow
- firopow
- geek, ghostrider, glt-astralhash, glt-globalhash, glt-jeonghash, glt-padihash, glt-pawelhash
- heavyhash, hex, hmq1725
- kawpow
- lyra2tdc, lyra2v2, lyra2v3, lyra2vc0ban
- megabtx
- nexapow, nist5
- phi, phi5, progpowz, progpow-ethercore, progpow-sero, progpow-veil, pufferfish2
- quark, quibit
- rwahash
- sha256, sha256csm, sha256d, sha256q, sha256t, sha512256d, shandwich256, skein2, skunkhash, skydoge
- timetravel, tribus
- vprogpow
- x11, x11k, x12, x13, x14, x15, x16r, x16rv2, x16rt, x16s, x17, x18, x20r, x21s, x22i, x25x, x33, xevan

# DEV-FEE:
- **0.75%**:
  - evrprogpow
  - firopow
  - heavyhash
  - kawpow
  - nexapow
  - progpowz
  - sha512256d
  - skein2
  - and all other non-listed below algorithms
- **1.00%**:
  - curvehash
  - ghostrider
  - mike
  - pufferfish2
- **2.00%**:
  - rwahash
  - sha256csm
  - skydoge

# OPTIONS
```
Usage: wildrig [OPTIONS]

Options:
  -a, --algo ALGO               specify the hash algorithm to use

      --benchmark                run offline benchmark
      --benchmark-hashorder      run offline benchmark and/or set hash order for benchmark
      --benchmark-epoch          run offline benchmark and/or set epoch for benchmark
      --benchmark-block          run offline benchmark and/or set block for benchmark
      --benchmark-timeout        run offline benchmark and/or set how long to run benchmark in seconds(default: 0)

  -o, --url URL                  URL of mining server
      --proxy                    set ip:port to connect via SOCKS5 proxy
  -O, --userpass U:P             username:password pair for mining server
  -u, --user USERNAME            username for mining server
  -p, --pass PASSWORD            password for mining server
  -w, --worker WORKERNAME        worker name(progpow variants only)
  -r, --retries N                number of times to retry before switch to backup server (default: 1)
  -R, --retry-pause N            time to pause between retries (default: 5)
      --max-rejects N            number of one by one rejects before switch to backup server (default: 5)
      --max-difficulty N         maximum difficulty to accept from pool(unit: M), otherwise reconnect (default: 0)

      --send-stale               send stale shares
      --diff-factor N            difficulty factor to use instead of algo default(default: 0)
      --no-extranonce            disable exranonce subscription
      --protocol PROTOCOL        set stratum protocol(ethproxy, ethstratum, stratum, stratum1, stratum2)

      --watchdog                 enable checking how long videocards are running OpenCL kernel(terminate if more than 30 sec.)
      --watchdog-script FILE     set file to execute when watchdog triggers(can be used without --watchdog parameter)
      --strategy N               strategy of feeding videocards with job(default: 0)
      --split-job N              set amount of gpu's(or threads of it, keep this in mind) solving one job

      --opencl-platforms N       list of OpenCL platforms to use(also possible to set amd or nvidia; default: all)
  -d, --opencl-devices N         list of OpenCL devices to use(default: all)
      --opencl-threads N         amount of threads per OpenCL device(default: auto)
  -i, --opencl-launch IxW        list of launch config, intensity and worksize(default: auto)
      --opencl-affinity N        affine GPU threads to a CPU
      --ptx-version N            specify what PTX ISA version to use(numbers should be without dot, e.g. 50, 63, 70 and so on)
      --progpow-kernel           depends on drivers values 1 or 2 can provide better hashrate for ProgPow(default: 0)
      --no-dag-split             disable splitting DAG on two parts(have sense only if AMD fix this problem in their drivers)
      --print-platforms          print available OpenCL platforms and exit
      --print-devices            print available OpenCL devices and exit

      --no-adl                   disable monitoring via ADL
      --no-igcl                  disable monitoring via IGCL
      --no-nvml                  disable monitoring via NVML
      --no-sysfs                 disable monitoring via sysfs
      --gpu-temp-limit N         set temperature at which gpu will stop mining(default: 85)
      --gpu-temp-resume N        set temperature at which gpu will resume mining(default: 60)

  Parameters below can be set for a list of GPU's, use comma to separate them and * to skip
      --gpu-core-clock N         lock GPU core clock to N
      --gpu-core-offset N        set offset N for GPU core clock
      --gpu-memory-clock N       lock GPU memory clock to N
      --gpu-memory-offset N      set offset N for GPU memory clock
      --gpu-powerlimit N         set power limit for GPU to N

      --execute-at-start COMMAND execute custom command before gpu initialization
      --execute COMMAND          execute custom command after gpu initialization or precompute stage, etc.
      --execute-wait N           wait for N seconds after executing the command (default: 1)

      --multiple-instance        allow multiple instances running at one time
  -l, --log-file FILE            log all output to a file

      --no-color                 disable colored output
      --print-time N             print hashrate report every N seconds
      --print-debug              print debug information

      --api-port N               port for API
      --api-worker-id ID         custom worker-id for API

  -h, --help                     display this help and exit
  -V, --version                  output version information and exit
```
