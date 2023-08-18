# Instructions specification

Each instruction is defined with a dictonary of parameters ([rocket-chip/IDecode.scala at v1.6 · chipsalliance/rocket-chip · GitHub](https://github.com/chipsalliance/rocket-chip/blob/v1.6/src/main/scala/rocket/IDecode.scala#L50)). Here is a summary for the RVI subset:

|     |        | legal | fp  | rocc | branch | jal | jalr | rxs2 | rxs1 | scie | sel_alu2 | sel_alu1 | sel_imm | alu_dw | alu_fn  | mem | mem_cmd | rfs1 | rfs2 | rfs3 | wfd | mul | div | wxd | csr   | fence_i | fence | amo | dp  |
|:--- |:------ |:----- |:--- |:---- |:------ |:--- |:---- |:---- |:---- |:---- |:-------- |:-------- |:------- |:------ |:------- |:--- |:------- |:---- |:---- |:---- |:--- |:--- |:--- |:--- |:----- |:------- |:----- |:--- |:--- |
| RVI | BNE    | Y     | N   | N    | Y      | N   | N    | Y    | Y    | N    | A2_RS2   | A1_RS1   | IMM_SB  | DW_X   | FN_SNE  | N   | M_X     | N    | N    | N    | N   | N   | N   | N   | CSR.N | N       | N     | N   | N   |
|     | BEQ    | Y     | N   | N    | Y      | N   | N    | Y    | Y    | N    | A2_RS2   | A1_RS1   | IMM_SB  | DW_X   | FN_SEQ  | N   | M_X     | N    | N    | N    | N   | N   | N   | N   | CSR.N | N       | N     | N   | N   |
|     | BLT    | Y     | N   | N    | Y      | N   | N    | Y    | Y    | N    | A2_RS2   | A1_RS1   | IMM_SB  | DW_X   | FN_SLT  | N   | M_X     | N    | N    | N    | N   | N   | N   | N   | CSR.N | N       | N     | N   | N   |
|     | BLTU   | Y     | N   | N    | Y      | N   | N    | Y    | Y    | N    | A2_RS2   | A1_RS1   | IMM_SB  | DW_X   | FN_SLTU | N   | M_X     | N    | N    | N    | N   | N   | N   | N   | CSR.N | N       | N     | N   | N   |
|     | BGE    | Y     | N   | N    | Y      | N   | N    | Y    | Y    | N    | A2_RS2   | A1_RS1   | IMM_SB  | DW_X   | FN_SGE  | N   | M_X     | N    | N    | N    | N   | N   | N   | N   | CSR.N | N       | N     | N   | N   |
|     | BGEU   | Y     | N   | N    | Y      | N   | N    | Y    | Y    | N    | A2_RS2   | A1_RS1   | IMM_SB  | DW_X   | FN_SGEU | N   | M_X     | N    | N    | N    | N   | N   | N   | N   | CSR.N | N       | N     | N   | N   |
|     | JAL    | Y     | N   | N    | N      | Y   | N    | N    | N    | N    | A2_SIZE  | A1_PC    | IMM_UJ  | DW_XPR | FN_ADD  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | JALR   | Y     | N   | N    | N      | N   | Y    | N    | Y    | N    | A2_IMM   | A1_RS1   | IMM_I   | DW_XPR | FN_ADD  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | AUIPC  | Y     | N   | N    | N      | N   | N    | N    | N    | N    | A2_IMM   | A1_PC    | IMM_U   | DW_XPR | FN_ADD  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | LB     | Y     | N   | N    | N      | N   | N    | N    | Y    | N    | A2_IMM   | A1_RS1   | IMM_I   | DW_XPR | FN_ADD  | Y   | M_XRD   | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | LH     | Y     | N   | N    | N      | N   | N    | N    | Y    | N    | A2_IMM   | A1_RS1   | IMM_I   | DW_XPR | FN_ADD  | Y   | M_XRD   | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | LW     | Y     | N   | N    | N      | N   | N    | N    | Y    | N    | A2_IMM   | A1_RS1   | IMM_I   | DW_XPR | FN_ADD  | Y   | M_XRD   | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | LBU    | Y     | N   | N    | N      | N   | N    | N    | Y    | N    | A2_IMM   | A1_RS1   | IMM_I   | DW_XPR | FN_ADD  | Y   | M_XRD   | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | LHU    | Y     | N   | N    | N      | N   | N    | N    | Y    | N    | A2_IMM   | A1_RS1   | IMM_I   | DW_XPR | FN_ADD  | Y   | M_XRD   | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | SB     | Y     | N   | N    | N      | N   | N    | Y    | Y    | N    | A2_IMM   | A1_RS1   | IMM_S   | DW_XPR | FN_ADD  | Y   | M_XWR   | N    | N    | N    | N   | N   | N   | N   | CSR.N | N       | N     | N   | N   |
|     | SH     | Y     | N   | N    | N      | N   | N    | Y    | Y    | N    | A2_IMM   | A1_RS1   | IMM_S   | DW_XPR | FN_ADD  | Y   | M_XWR   | N    | N    | N    | N   | N   | N   | N   | CSR.N | N       | N     | N   | N   |
|     | SW     | Y     | N   | N    | N      | N   | N    | Y    | Y    | N    | A2_IMM   | A1_RS1   | IMM_S   | DW_XPR | FN_ADD  | Y   | M_XWR   | N    | N    | N    | N   | N   | N   | N   | CSR.N | N       | N     | N   | N   |
|     | LUI    | Y     | N   | N    | N      | N   | N    | N    | N    | N    | A2_IMM   | A1_ZERO  | IMM_U   | DW_XPR | FN_ADD  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | ADDI   | Y     | N   | N    | N      | N   | N    | N    | Y    | N    | A2_IMM   | A1_RS1   | IMM_I   | DW_XPR | FN_ADD  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | SLTI   | Y     | N   | N    | N      | N   | N    | N    | Y    | N    | A2_IMM   | A1_RS1   | IMM_I   | DW_XPR | FN_SLT  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | SLTIU  | Y     | N   | N    | N      | N   | N    | N    | Y    | N    | A2_IMM   | A1_RS1   | IMM_I   | DW_XPR | FN_SLTU | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | ANDI   | Y     | N   | N    | N      | N   | N    | N    | Y    | N    | A2_IMM   | A1_RS1   | IMM_I   | DW_XPR | FN_AND  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | ORI    | Y     | N   | N    | N      | N   | N    | N    | Y    | N    | A2_IMM   | A1_RS1   | IMM_I   | DW_XPR | FN_OR   | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | XORI   | Y     | N   | N    | N      | N   | N    | N    | Y    | N    | A2_IMM   | A1_RS1   | IMM_I   | DW_XPR | FN_XOR  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | ADD    | Y     | N   | N    | N      | N   | N    | Y    | Y    | N    | A2_RS2   | A1_RS1   | IMM_X   | DW_XPR | FN_ADD  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | SUB    | Y     | N   | N    | N      | N   | N    | Y    | Y    | N    | A2_RS2   | A1_RS1   | IMM_X   | DW_XPR | FN_SUB  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | SLT    | Y     | N   | N    | N      | N   | N    | Y    | Y    | N    | A2_RS2   | A1_RS1   | IMM_X   | DW_XPR | FN_SLT  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | SLTU   | Y     | N   | N    | N      | N   | N    | Y    | Y    | N    | A2_RS2   | A1_RS1   | IMM_X   | DW_XPR | FN_SLTU | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | AND    | Y     | N   | N    | N      | N   | N    | Y    | Y    | N    | A2_RS2   | A1_RS1   | IMM_X   | DW_XPR | FN_AND  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | OR     | Y     | N   | N    | N      | N   | N    | Y    | Y    | N    | A2_RS2   | A1_RS1   | IMM_X   | DW_XPR | FN_OR   | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | XOR    | Y     | N   | N    | N      | N   | N    | Y    | Y    | N    | A2_RS2   | A1_RS1   | IMM_X   | DW_XPR | FN_XOR  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | SLL    | Y     | N   | N    | N      | N   | N    | Y    | Y    | N    | A2_RS2   | A1_RS1   | IMM_X   | DW_XPR | FN_SL   | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | SRL    | Y     | N   | N    | N      | N   | N    | Y    | Y    | N    | A2_RS2   | A1_RS1   | IMM_X   | DW_XPR | FN_SR   | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | SRA    | Y     | N   | N    | N      | N   | N    | Y    | Y    | N    | A2_RS2   | A1_RS1   | IMM_X   | DW_XPR | FN_SRA  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.N | N       | N     | N   | N   |
|     | FENCE  | Y     | N   | N    | N      | N   | N    | N    | N    | N    | A2_X     | A1_X     | IMM_X   | DW_X   | FN_X    | N   | M_X     | N    | N    | N    | N   | N   | N   | N   | CSR.N | N       | Y     | N   | N   |
|     | SCALL  | Y     | N   | N    | N      | N   | N    | N    | X    | N    | A2_X     | A1_X     | IMM_X   | DW_X   | FN_X    | N   | M_X     | N    | N    | N    | N   | N   | N   | N   | CSR.I | N       | N     | N   | N   |
|     | SBREAK | Y     | N   | N    | N      | N   | N    | N    | X    | N    | A2_X     | A1_X     | IMM_X   | DW_X   | FN_X    | N   | M_X     | N    | N    | N    | N   | N   | N   | N   | CSR.I | N       | N     | N   | N   |
|     | MRET   | Y     | N   | N    | N      | N   | N    | N    | X    | N    | A2_X     | A1_X     | IMM_X   | DW_X   | FN_X    | N   | M_X     | N    | N    | N    | N   | N   | N   | N   | CSR.I | N       | N     | N   | N   |
|     | WFI    | Y     | N   | N    | N      | N   | N    | N    | X    | N    | A2_X     | A1_X     | IMM_X   | DW_X   | FN_X    | N   | M_X     | N    | N    | N    | N   | N   | N   | N   | CSR.I | N       | N     | N   | N   |
|     | CEASE  | Y     | N   | N    | N      | N   | N    | N    | X    | N    | A2_X     | A1_X     | IMM_X   | DW_X   | FN_X    | N   | M_X     | N    | N    | N    | N   | N   | N   | N   | CSR.I | N       | N     | N   | N   |
|     | CSRRW  | Y     | N   | N    | N      | N   | N    | N    | Y    | N    | A2_ZERO  | A1_RS1   | IMM_X   | DW_XPR | FN_ADD  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.W | N       | N     | N   | N   |
|     | CSRRS  | Y     | N   | N    | N      | N   | N    | N    | Y    | N    | A2_ZERO  | A1_RS1   | IMM_X   | DW_XPR | FN_ADD  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.S | N       | N     | N   | N   |
|     | CSRRC  | Y     | N   | N    | N      | N   | N    | N    | Y    | N    | A2_ZERO  | A1_RS1   | IMM_X   | DW_XPR | FN_ADD  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.C | N       | N     | N   | N   |
|     | CSRRWI | Y     | N   | N    | N      | N   | N    | N    | N    | N    | A2_IMM   | A1_ZERO  | IMM_Z   | DW_XPR | FN_ADD  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.W | N       | N     | N   | N   |
|     | CSRRSI | Y     | N   | N    | N      | N   | N    | N    | N    | N    | A2_IMM   | A1_ZERO  | IMM_Z   | DW_XPR | FN_ADD  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.S | N       | N     | N   | N   |
|     | CSRRCI | Y     | N   | N    | N      | N   | N    | N    | N    | N    | A2_IMM   | A1_ZERO  | IMM_Z   | DW_XPR | FN_ADD  | N   | M_X     | N    | N    | N    | N   | N   | N   | Y   | CSR.C | N       | N     | N   | N   |

For the Rocket Chip, we can see that due to the modular structure of the RISC-V ISA, each subset is a new class which is added or not to the CPU thanks to input parameters.

These parameters can be explained as follows:

| Paramètre   | Description                                                             |
|:---------   |:----------------------------------------------------------------------- |
| `legal`     | Valid instruction                                                       |
| `fp`        | Floating point                                                          |
| `rocc`      | RoCC (Rocket Custom Coprocessor)                                        |
| `branch`    | Branch                                                                  |
| `jal`       | Jump and link                                                           |
| `jalr`      | Jump and link register                                                  |
| `rxs2`      | Instruction using rs2 : BEQ rs1, rs2, imm ou XOR rd, rs1, rs2           |
| `rxs1`      | Instruction using rs1 : BEQ rs1, rs2, imm ou LB rd, rs1, imm            |
| `scie`      | SCIE = Sifive Custom Instruction Extension. Only one instruction use it |
| `sel_alu2`  | Operand 2 for ALU (if needed)                                           |
| `sel_alu1`  | Operand 1 for ALU (if needed)                                           |
| `sel_imm`   | Immediate for ALU (if needed)                                           |
| `alu_dw`    | Data width for ALU                                                      |
| `alu_fn`    | Function used in ALU                                                    |
| `mem`       | Memory-related instructions                                             |
| `mem_cmd`   | Specify a given memory operation (load, store...)                       |
| `rfs1`      | Only used in floating-related instructions                              |
| `rfs2`      | Only used in floating-related instructions                              |
| `rfs3`      | Not used, probably for future use                                       |
| `wfd`       | Used to log some flaoting-related events                                |
| `mul`       | Multiplication (M) ou something else (N)                                |
| `div`       | Division (Y) ou multiplication (D)                                      |
| `wxd`       | Usef for logging                                                        |
| `csr`       | CSR.N for instructions not related to CSR                               |
| `fence_i`   | Only for the `fence_i` instruction                                      |
| `fence`     | Only for the `fence` instruction                                        |
| `amo`       | Atomic extension                                                        |
| `dp`        | Double-precision extension                                              |
