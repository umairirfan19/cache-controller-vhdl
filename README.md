# CPU Cache Controller in VHDL (COE758 Project)

This project implements a **direct-mapped cache controller** in **VHDL** for a simple CPU system as part of the **COE758 – Digital Systems Engineering** course at Toronto Metropolitan University.

The design models a basic memory hierarchy consisting of:
- CPU issuing read/write requests
- Cache controller with local BlockRAM
- External SDRAM memory controller

The cache sits between the CPU and SDRAM and handles address decoding, hit/miss detection, data transfers, and dirty-block write-back.

---

## 📐 Cache Specification

| Feature | Value |
|--------|-------|
Cache size | 256 bytes |
Block size | 32 bytes |
Cache lines | 8 |
Word size | 1 byte |
Associativity | Direct mapped |
CPU Address width | 16 bits |
Address breakdown | Tag (8 bits), Index (3 bits), Offset (5 bits) |

---

## ⚙️ Functional Behavior

The cache controller handles 4 main cases:

| Case | Behavior |
|------|---------|
Read hit | Return data from cache |
Write hit | Update cache, set dirty bit |
Miss & dirty = 0 | Load block from SDRAM and update tag/valid bits |
Miss & dirty = 1 | Write back old block to SDRAM, then load new block |

The design interacts with the CPU, BlockRAM, and SDRAM according to the timing and control signals defined in the COE758 project specification :contentReference[oaicite:0]{index=0}.

---

## 📂 Files Included

| File | Description |
|------|------------|
`CacheController.vhd` | Main cache controller |
`CPU_gen.vhd` | CPU request generator |
`SDRAMController.vhd` | SDRAM memory controller |
`TEST.vhd` | Testbench for simulation |

---

## 🧪 Simulation

The design was verified using VHDL behavioral simulation by:

- Generating CPU read/write requests
- Monitoring cache hit/miss behavior
- Observing block transfers to/from SDRAM
- Verifying correct tag, valid, and dirty bit operation

---

## 🛠 Tools Used

- Xilinx ISE / ISim
- VHDL
- Spartan-3E FPGA platform (course hardware)

---

## 📎 Course

**COE758 — Digital Systems Engineering**  
Toronto Metropolitan University (TMU)

