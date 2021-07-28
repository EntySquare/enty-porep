# Storage Proofs PoRep

EntySquare official replication with cores sharing L3-cache binding through Kubernetes 

CCD / CCX groups listed with AMD 7002 series CPUs needed

    #> root@I01-64-009:~# lscpu
    Architecture:        x86_64
    CPU op-mode(s):      32-bit, 64-bit
    Byte Order:          Little Endian
    CPU(s):              128
    On-line CPU(s) list: 0-127
    Thread(s) per core:  2
    Core(s) per socket:  32
    Socket(s):           2
    NUMA node(s):        2
    Vendor ID:           AuthenticAMD
    CPU family:          23
    Model:               49
    Model name:          AMD EPYC 7542 32-Core Processor
    Stepping:            0
    CPU MHz:             1495.537
    CPU max MHz:         2900.0000
    CPU min MHz:         1500.0000
    BogoMIPS:            5789.00
    Virtualization:      AMD-V
    L1d cache:           32K
    L1i cache:           32K
    L2 cache:            512K
    L3 cache:            16384K
    NUMA node0 CPU(s):   0-31,64-95
    NUMA node1 CPU(s):   32-63,96-127
    Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx cpb cat_l3 cdp_l3 hw_pstate sme ssbd mba sev ibrs ibpb stibp vmmcall fsgsbase bmi1 avx2 smep bmi2 cqm rdt_a rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local clzero irperf xsaveerptr wbnoinvd arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif umip rdpid overflow_recov succor smca

Using hwloc-ls command on cli to check whether L3-cache is shared through four cores with one CCX chipset.

    Machine (2012GB total)
    NUMANode L#0 (P#0 1004GB)
    Package L#0
    L3 L#0 (16MB)
    L2 L#0 (512KB) + L1d L#0 (32KB) + L1i L#0 (32KB) + Core L#0
    PU L#0 (P#0)
    PU L#1 (P#64)
    L2 L#1 (512KB) + L1d L#1 (32KB) + L1i L#1 (32KB) + Core L#1
    PU L#2 (P#1)
    PU L#3 (P#65)
    L2 L#2 (512KB) + L1d L#2 (32KB) + L1i L#2 (32KB) + Core L#2
    PU L#4 (P#2)
    PU L#5 (P#66)
    L2 L#3 (512KB) + L1d L#3 (32KB) + L1i L#3 (32KB) + Core L#3
    PU L#6 (P#3)
    PU L#7 (P#67)
    .
    .
    .
    
### In order to keep right core Indexes, you'll need to set CPU_GROUP_INDEX manually. But if you're using enty-fil-miner, it's automatically done by Kubernetes.

## License

MIT or Apache 2.0
