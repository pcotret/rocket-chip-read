This module contains:
- Instructions encoding (alphabetical order, all extensions)
- Exception IDs
- CSR addresses

## Exception IDs

| Exception | Value | Description |
| --- | --- | --- |
| misaligned_fetch | 0x0 | Instruction address misaligned |
| fetch_access | 0x1 | Instruction access fault |
| illegal_instruction | 0x2 | Illegal instruction |
| breakpoint | 0x3 | Breakpoint |
| misaligned_load | 0x4 | Load address misaligned |
| load_access | 0x5 | Load access fault |
| misaligned_store | 0x6 | Store/AMO address misaligned |
| store_access | 0x7 | Store/AMO access fault |
| user_ecall | 0x8 | Environment call from U-mode or VU-mode |
| supervisor_ecall | 0x9 | Environment call from HS-mode |
| virtual_supervisor_ecall | 0xa | Environment call from VS-mode |
| machine_ecall | 0xb | Environment call from M-mode |
| fetch_page_fault | 0xc | Instruction page fault |
| load_page_fault | 0xd | Load page fault |
| store_page_fault | 0xf | Store/AMO page fault |
| fetch_guest_page_fault | 0x14 | Instruction guest-page fault |
| load_guest_page_fault | 0x15 | Load guest-page fault |
| virtual_instruction | 0x16 | Virtual instruction |
| store_guest_page_fault | 0x17 | Store/AMO guest-page fault |

> Source: [RISC-V Priviledged architecture - Table 8.6](https://riscv.org/technical/specifications/)

## CSR addresses
| Name | Address |
| ---  | ---     |
| fflags | 0x1 |
| frm | 0x2 |
| fcsr | 0x3 |
| vstart | 0x8 |
| vxsat | 0x9 |
| vxrm | 0xa |
| vcsr | 0xf |
| seed | 0x15 |
| cycle | 0xc00 |
| time | 0xc01 |
| instret | 0xc02 |
| [hpmcounter3-hpmcounter31] | [0xc03-0xc1f] |
| vl | 0xc20 |
| vtype | 0xc21 |
| vlenb | 0xc22 |
| sstatus | 0x100 |
| sedeleg | 0x102 |
| sideleg | 0x103 |
| sie | 0x104 |
| stvec | 0x105 |
| scounteren | 0x106 |
| senvcfg | 0x10a |
| sscratch | 0x140 |
| sepc | 0x141 |
| scause | 0x142 |
| stval | 0x143 |
| sip | 0x144 |
| satp | 0x180 |
| scontext | 0x5a8 |
| vsstatus | 0x200 |
| vsie | 0x204 |
| vstvec | 0x205 |
| vsscratch | 0x240 |
| vsepc | 0x241 |
| vscause | 0x242 |
| vstval | 0x243 |
| vsip | 0x244 |
| vsatp | 0x280 |
| hstatus | 0x600 |
| hedeleg | 0x602 |
| hideleg | 0x603 |
| hie | 0x604 |
| htimedelta | 0x605 |
| hcounteren | 0x606 |
| hgeie | 0x607 |
| henvcfg | 0x60a |
| htval | 0x643 |
| hip | 0x644 |
| hvip | 0x645 |
| htinst | 0x64a |
| hgatp | 0x680 |
| hcontext | 0x6a8 |
| hgeip | 0xe12 |
| utvt | 0x7 |
| unxti | 0x45 |
| uintstatus | 0x46 |
| uscratchcsw | 0x48 |
| uscratchcswl | 0x49 |
| stvt | 0x107 |
| snxti | 0x145 |
| sintstatus | 0x146 |
| sscratchcsw | 0x148 |
| sscratchcswl | 0x149 |
| mtvt | 0x307 |
| mnxti | 0x345 |
| mintstatus | 0x346 |
| mscratchcsw | 0x348 |
| mscratchcswl | 0x349 |
| mstatus | 0x300 |
| misa | 0x301 |
| medeleg | 0x302 |
| mideleg | 0x303 |
| mie | 0x304 |
| mtvec | 0x305 |
| mcounteren | 0x306 |
| menvcfg | 0x30a |
| mcountinhibit | 0x320 |
| mscratch | 0x340 |
| mepc | 0x341 |
| mcause | 0x342 |
| mtval | 0x343 |
| mip | 0x344 |
| mtinst | 0x34a |
| mtval2 | 0x34b |
| [pmpcfg0-pmpcfg15] | [0x3a0-0x3af] |
| [pmpaddr0-pmpaddr63] | [0x3b0-0x3ef] |
| mseccfg | 0x747 |
| tselect | 0x7a0 |
| tdata1 | 0x7a1 |
| tdata2 | 0x7a2 |
| tdata3 | 0x7a3 |
| tinfo | 0x7a4 |
| tcontrol | 0x7a5 |
| mcontext | 0x7a8 |
| mscontext | 0x7aa |
| dcsr | 0x7b0 |
| dpc | 0x7b1 |
| dscratch0 | 0x7b2 |
| dscratch1 | 0x7b3 |
| mcycle | 0xb00 |
| minstret | 0xb02 |
| [mhpmcounter3-mhpmcounter31] | [0xb03-0xb1f] |
| [mhpmevent3-mhpmevent31] | [0x323-0x33f] |
| mvendorid | 0xf11 |
| marchid | 0xf12 |
| mimpid | 0xf13 |
| mhartid | 0xf14 |
| mconfigptr | 0xf15 |
| htimedeltah | 0x615 |
| henvcfgh | 0x61a |
| cycleh | 0xc80 |
| timeh | 0xc81 |
| instreth | 0xc82 |
| [hpmcounter3h-hpmcounter31h] | [0xc83-0xc9f] |
| mstatush | 0x310 |
| menvcfgh | 0x31a |
| mseccfgh | 0x757 |
| mcycleh | 0xb80 |
| minstreth | 0xb82 |
| [mhpmcounter3h-mhpmcounter31h] | [0xb83-0xb9f] |