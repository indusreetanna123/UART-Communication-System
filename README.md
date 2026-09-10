# UART FIFO Communication System in Verilog

A Verilog-based UART communication system that combines a **FIFO buffer** with **UART transmitter and receiver** modules. The design was developed and functionally verified using **Xilinx Vivado behavioral simulation**.

The system stores multiple bytes in a FIFO and transmits them sequentially through UART. The transmitted data is received back through the UART receiver and verified using a testbench.

---

## 📌 Project Overview

This project demonstrates the integration of:

- FIFO memory
- UART Transmitter (TX)
- UART Receiver (RX)
- Control logic / FSM
- Verilog testbench
- Behavioral simulation and waveform verification

The main purpose of the project is to understand how a FIFO can be used to buffer data before sending it through a UART communication interface.

### Data Flow

```text
                  +----------------+
                  |   Input Data   |
                  |  8-bit data    |
                  +-------+--------+
                          |
                          | wr_en
                          v
                  +----------------+
                  |      FIFO      |
                  |                |
                  | Depth = 16     |
                  | Width = 8 bits |
                  +-------+--------+
                          |
                          | FIFO Read
                          v
                  +----------------+
                  |  Control FSM   |
                  +-------+--------+
                          |
                          | tx_start
                          v
                  +----------------+
                  |    UART TX     |
                  |   9600 Baud    |
                  +-------+--------+
                          |
                          | tx
                          v
                  +----------------+
                  |    UART RX     |
                  |   9600 Baud    |
                  +-------+--------+
                          |
                          | rx_done
                          v
                  +----------------+
                  | Received Data  |
                  +----------------+