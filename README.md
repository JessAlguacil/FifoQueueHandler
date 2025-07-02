# FIFO Queue Handler (Structured Text)

A reusable and optimized FIFO queue implementation written in **IEC 61131-3 Structured Text**.  
Ideal for industrial automation projects where multiple request channels must be handled fairly, but only a limited number can be active at the same time.

---

## 🚀 Features

- ✅ Designed for **FPWIN Pro 7 (Panasonic)**
- ✅ Designed for **TIA PORTAL V16 OR Later (Siemens)**
- ✅ Designed for **SYSMAC STUDIO (Omron)**
- 📦 Generic FIFO queue logic (supports motors, valves, stations, etc.)
- 🌀 Circular input scan (1 channel processed per scan cycle)
- ⚙️ Configurable:
  - Queue length
  - Max number of active requests
- 🛡️ Prevents duplicate entries in queue
- 🔧 Minimal CPU usage, scalable to 20+ channels
- 🧩 Easily portable to other IEC 61131-3 environments (TwinCAT, CODESYS, etc.)

- ## 🧠 Interface Overview

This section describes the input and output variables of the `FifoQueueHandler` function block.

### 📥 Inputs (`DataIn` structure)
| Variable | Type | Description |
|----------|------|-------------|
| `QueueLength`         | `INT`     | Maximum number of elements allowed in the queue. |
| `MaxActiveRequests`   | `INT`     | Maximum number of simultaneous active requests (e.g., 3). |
| `Input[0..N-1]`       | `ARRAY OF BOOL` | Input request signals (one per channel). |

### 📤 Outputs
| Variable | Type | Description |
|----------|------|-------------|
| `DataQ[0..N-1]`        | `ARRAY OF BOOL` | Output activation signals for each channel. |
| `QueueSize`           | `INT`            | Current number of entries in the queue. |
| `ChannelData[].Active` | `BOOL` (internal structure) | TRUE if the channel is currently active. |

> ℹ️ *Note: The `ChannelData[]` structure is handled internally but can be inspected if the FB is used in an open project (not just via library).*

---

### 🔧 Example Variable Declaration (Sysmac Studio)

When using the FB from a library in Sysmac Studio, declare your variables like this:

```structured-text
VAR
    MyFifo      : FifoQueueHandler;
    Inputs      : ARRAY[0..9] OF BOOL;      // 10 input requests
    Outputs     : ARRAY[0..9] OF BOOL;
    Config      : STRUCT
        QueueLength       : INT := 10;
        MaxActiveRequests : INT := 3;
        Input             : ARRAY[0..9] OF BOOL;
    END_STRUCT;
END_VAR


MyFifo(Config,Outputs); // Function block declared in the Main block

