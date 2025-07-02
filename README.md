# FIFO Queue Handler (Structured Text) for FPWIN Pro 7 (Panasonic)

A reusable and optimized FIFO queue implementation written in **IEC 61131-3 Structured Text**, designed specifically for **FPWIN Pro 7 (Panasonic)**.  
Ideal for industrial automation projects where multiple request channels must be handled fairly, but only a limited number can be active at the same time.

---

## 🚀 Features

- ✅ Designed for **FPWIN Pro 7 (Panasonic)**
- 📦 Generic FIFO queue logic (supports motors, valves, stations, etc.)
- 🌀 Circular input scan (1 channel processed per scan cycle)
- ⚙️ Configurable:
  - Queue length
  - Max number of active requests
- 🛡️ Prevents duplicate entries in queue
- 🔧 Minimal CPU usage, scalable to 20+ channels
- 🧩 Easily portable to other IEC 61131-3 environments (TwinCAT, CODESYS, etc.)
