# AMBA-AXI4-Stream-AXIS-Protocol
AXI4-Stream (AXIS) is a unidirectional streaming protocol from **ARM's AMBA** family for moving data between IP blocks in FPGAs/SoCs. It uses a TVALID/TREADY handshake with optional TLAST, TKEEP, and TUSER for packet boundaries, byte qualifiers, and metadata, ideal for video, DMA, and accelerators.
## Overview
AXI4-Stream (AXIS) is a lightweight, unidirectional streaming protocol from ARM’s AMBA family. It is widely used to pass continuous or packetized data between IP blocks inside FPGAs/SoCs (for example, DMA engines, hardware accelerators, video pipelines, and network stacks).

Unlike memory-mapped AXI, AXIS contains no addresses — it only transports data, optional sideband signals, and packet boundary markers. The fundamental mechanism uses a **TVALID / TREADY** handshake to move data safely between a transmitter (master) and a receiver (slave).

## Key signals
The following are the most commonly used AXIS signals (names shown as typical `S_AXIS_ / `M_AXIS_ port names):
