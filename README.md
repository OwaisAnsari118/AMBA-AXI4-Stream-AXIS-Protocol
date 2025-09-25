# AMBA-AXI4-Stream-AXIS-Protocol
AXI4-Stream (AXIS) is a unidirectional streaming protocol from **ARM's AMBA** family for moving data between IP blocks in FPGAs/SoCs. It uses a TVALID/TREADY handshake with optional TLAST, TKEEP, and TUSER for packet boundaries, byte qualifiers, and metadata, ideal for video, DMA, and accelerators.
## Overview
AXI4-Stream (AXIS) is a lightweight, unidirectional streaming protocol from ARM’s AMBA family. It is widely used to pass continuous or packetized data between IP blocks inside FPGAs/SoCs (for example, DMA engines, hardware accelerators, video pipelines, and network stacks).

Unlike memory-mapped AXI, AXIS contains no addresses — it only transports data, optional sideband signals, and packet boundary markers. The fundamental mechanism uses a **TVALID / TREADY** handshake to move data safely between a transmitter (master) and a receiver (slave).

## Key signals
The following are the most commonly used AXIS signals (names shown as typical `S_AXIS_` / `M_AXIS_` port names):

| Signal           | Source | Width           | Description                                                                                      |
| `TDATA`          | Master | `TDATA_WIDTH`   | Primary data payload (must be an integer number of bytes)                                        | 
| `TVALID`         | Master | 1               | Indicates the master drivers valid data this cycle                                               |
| `TREADY`         | Slave  | 1               | Indicates the slave is ready to accept data this cycle                                           |
| `TLAST`          | Master | 1               | Marks the last beat of packet/frame                                                              |
| `TKEEP`/ `TSTRB` | Master | `TDATA_WIDTH/8` | Byte qualifiers indicate which bytes in `TDATA` are valid (TKEEP) or strobe qualifer (TSTRB)     |
| `TUSER`          | Master | `TUSER_WIDTH`   | User-defined sideband bits, e.g., start-of-frame, error flags                                    | 
| `TID`            | Master | `TID_WIDTH`     | Stream identifier for routing or multi-stream scenarios                                          |
| `TDEST`          | Master | `TDEST_WIDTH`   | Destination routing info for interconnnects                                                      |

**Implementation note: `TDATA_WIDTH` should be a whole number of bytes (8-bit multiples). Common widths: 8, 16, 32, 64, 128, 256, 512.**

