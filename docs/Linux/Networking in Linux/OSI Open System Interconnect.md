# OSI Open System Interconnect

## Layers

| Layer | Name | Description | Data Labels |
| --- | --- | --- | --- |
| 1   | Physical | Bits | Bits |
| 2   | Data Link | MAC | Frames |
| 3   | Network | IP  | Packets |
| 4   | Tranport | TCP or UDP | Segments |
| 5   | Session | Connection Controls | DATA |
| 6   | Presentation | Compression, Encryption controls | DATA |
| 7   | Application | App data | DATA |

---

### Physical Layer

Physical medium: cables, fibre optics, wireless

Convert digital data to signals

Voltage, modulation and synchronization

Physical layer cannot be controlled from software as we cannot plugin or unplug from software.

But we can enable or disable network device from software

`ip link set dev <interface> up` to enable

`ip link set dev <inetrfcae> down` to disable

To know the interfaces: `ip -br a show`

---

### Data link Layer

It defines who should receive data

#### Function:

- Organized data into frames
- Add source and destination MAC

It has 2 sub layers

1.  Logical Link Control (LLC)
    1.  Flow control and error detection
    2.  It connects to network layer
2.  Media Access Control (MAC)
    1.  Unique hardware addresses
    2.  Understand who is sender and receiver

#### MAC

Hexadecimal