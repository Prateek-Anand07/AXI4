# AXI4 & AXI4-Lite Bus Protocol RTL Design

**Overview**
This repository contains Register Transfer Level (RTL) hardware designs implementing the AMBA AXI4 and AXI4-Lite bus protocols, as well as the foundational Valid/Ready handshaking principles. The designs are structured progressively, with each module serving as a building block for the next, culminating in a robust communication framework for complex System-on-Chip (SoC) architectures.

## 1. Handshaking Communication Principle
In digital hardware design, handshaking is the fundamental mechanism that synchronizes data transfer across independent modules. This implementation utilizes a strict **Valid/Ready handshaking protocol**:
* **Valid:** Asserted by the source (sender) to indicate that the payload data on the bus is stable and valid.
* **Ready:** Asserted by the destination (receiver) to indicate it is available to accept new data.

A successful transaction only occurs on the clock edge where both `Valid` and `Ready` are asserted simultaneously. This coordinates flow control, ensures data integrity, and prevents data dropping between sender and receiver.

## 2. AXI4-Lite Bus Protocol
AXI4-Lite is a streamlined, lightweight variant of the full AXI4 protocol, tailored for simple control-register interfaces and low-bandwidth peripherals. 
* **Design Focus:** It minimizes resource usage and gate count by offering a simpler interface compared to full AXI4.
* **Capabilities:** Operates using single-beat data transfers, intentionally omitting complex features like bursts or out-of-order completion. 
* **Use Case:** Ideal for memory-mapped peripherals that require a straightforward, low-complexity communication interface without the overhead of a high-throughput data pipeline.

## 3. AXI4 Bus Protocol (Full)
AXI4 (Advanced eXtensible Interface 4) is a high-performance, feature-rich protocol designed to serve as the high-bandwidth backbone for modern SoC architectures.
* **Design Focus:** Engineered to facilitate highly efficient, low-latency data pipelines between high-speed masters (e.g., processors, DMA controllers) and slaves (e.g., memory).
* **Capabilities:** Supports advanced hardware capabilities including burst transactions (up to 256 data transfers per burst), multiple outstanding addresses, and out-of-order transaction completion.
* **Use Case:** Provides a robust, scalable framework capable of meeting the high-bandwidth memory and subsystem communication requirements of advanced chip designs.

## References
- [Rules for Ready/Valid Handshakes](http://fpgacpu.ca/fpga/handshake.html)
- [AMBA AXI and ACE Protocol Specification (AXI3, AXI4, and AXI4-Lite)](http://www.gstitt.ece.ufl.edu/courses/fall15/eel4720_5721/labs/refs/AXI4_specification.pdf)
- [AXI4-Lite Interface Overview](https://www.realdigital.org/doc/a9fee931f7a172423e1ba73f66ca4081)