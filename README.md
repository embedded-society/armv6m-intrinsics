# armv6m-intrinsics

Header-only C++20 wrappers for ARMv6-M instructions that are not normally emitted by a C/C++ compiler — the C++ analogue of CMSIS-Core's `__NOP()`, `__WFI()`, `__DSB()`, etc.

Targets the **ARMv6-M** instruction set: Cortex-M0, Cortex-M0+, and Cortex-M1.

## Usage

Copy the library into your project (e.g., into `lib/`) and add it via CMake:

```cmake
add_subdirectory(lib/armv6m-intrinsics)
target_link_libraries(your_target PRIVATE armv6m-intrinsics)
```

Then include what you need:

```cpp
#include <armv6m-intrinsics/barriers.hpp>
#include <armv6m-intrinsics/interrupts.hpp>

void critical_section() {
    ArmCortex::asmCpsid();      // mask interrupts
    ArmCortex::asmDsb();        // ensure prior writes complete
    // ... protected work ...
    ArmCortex::asmCpsie();      // unmask interrupts
}
```

## Contents

| File | Instructions | Notes |
|------|--------------|-------|
| `hints.hpp` | `NOP`, `YIELD`, `WFI`, `WFE`, `SEV`, `BKPT<imm>` | Hint-class instructions; `BKPT` takes an 8-bit immediate identifier |
| `barriers.hpp` | `DSB`, `DMB`, `ISB` | Memory and instruction synchronisation barriers (full system domain) |
| `interrupts.hpp` | `CPSIE i`, `CPSID i` | Enable/disable maskable exceptions via PRIMASK |
| `svc.hpp` | `SVC<imm>` | Supervisor call with 8-bit immediate (template-encoded) |
| `reverse.hpp` | `REV`, `REV16`, `REVSH` | Byte-order reversal of word, halfword pairs, and signed lower halfword |

## Licence

This project is licensed under the Apache License Version 2.0.  
Copyright (C) 2026 The Embedded Society <https://github.com/embedded-society/armv6m-intrinsics>.  
See the attached [LICENCE](./LICENCE) file for more info.
