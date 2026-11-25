# systems speedrun ͙͘͡★.ᐣᝰ.ᐟ

**INTRO:**  Speedrunning through the computing stack for a classic hardware and RF/network hacker & tinkerer.

**RULES:**
- **Build then Theory:** Start at a terminal, a breadboard, or an antenna. Open a textbook or datasheet when I actually hit a wall.

---

<tt>˗ˏˋ ★ ˎˊ˗ `STAGE 0: REAL LINUX & BARE C`</tt>

- **OverTheWire: Bandit & CS50x Weeks 0–5** · [`open gist`](https://github.com)<br>
  Lock down shell survival, SSH, file permissions, and basic C memory/pointer.

- **Nand2Tetris PartS I & II**<br>
  Hardware Architecture (logic gates, CPU, assembler) &  Software Hierarchy (VM, compiler, OS)<br>
<a href="N2T1.pdf"><img src="https://img.shields.io/badge/Nand_to_Tetris-Part_1-0056D2?style=for-the-badge&logo=coursera&logoColor=white" alt="Nand to Tetris Part 1"></a> 
<a href="N2T2.pdf"><img src="https://img.shields.io/badge/Nand_to_Tetris-Part_2-0056D2?style=for-the-badge&logo=coursera&logoColor=white" alt="Nand to Tetris Part 2"></a>

 
- **Beej’s Guide to Network Programming** · [`open gist`](https://github.com)<br>
  Write pure C on Linux using POSIX sockets, file descriptors, and raw network I/O.<br>


<p align="center">•─────⋅ᓚᘏᗢ⋅──────────⋅ᓚᘏᗢ⋅──────────⋅ᓚᘏᗢ⋅─────•</p>

<tt>˗ˏˋ ★ ˎˊ˗ `STAGE 1: BARE-METAL HARDWARE`</tt>

- **Microcontroller SDKs (ESP32 / STM32 / RP2040)** · [`open gist`](https://github.com)<br>
  Ditch Arduino and MicroPython. Program directly in C using ESP-IDF, STM32 HAL/registers, or the Pico SDK.

- **Datasheets & Bus Protocols (UART, SPI, I2C)** · [`open gist`](https://github.com)<br>
  Configure hardware registers, handle interrupts, and sniff live pin traffic with a cheap \$10 logic analyzer.

<p align="center">•─────⋅ᓚᘏᗢ⋅──────────⋅ᓚᘏᗢ⋅──────────⋅ᓚᘏᗢ⋅─────•</p>

<tt>˗ˏˋ ★ ˎˊ˗ `STAGE 2: THE NETWORK STACK`</tt>

- **Stanford CS144 (Labs Only)** · [`open gist`](https://github.com)<br>
  Skip the lecture binge and implement a working TCP stack in C++ from scratch (sliding windows, retransmissions, and congestion control).<br>
  <a href="stage-2-network-stack/cs144-tcp/"><img src="https://shields.io" alt="Stanford CS144 TCP Labs"></a>

- **Linux Kernel Networking (`ip route`, `nftables`, `ip netns`)** · [`open gist`](https://github.com)<br>
  Turn a Linux box into a custom router using network namespaces and firewall rules.

<p align="center">•─────⋅ᓚᘏᗢ⋅──────────⋅ᓚᘏᗢ⋅──────────⋅ᓚᘏᗢ⋅─────•</p>

<tt>˗ˏˋ ★ ˎˊ˗ `STAGE 3: SIGNALS & RF`</tt>

- **RTL-SDR & Raw IQ Samples** · [`open gist`](https://github.com)<br>
  Plug in a \$30 RTL-SDR, open GNU Radio, or write Python/C scripts to pull raw IQ data straight from the air.<br>
  <a href="stage-3-signals-rf/rtl-sdr-iq/"><img src="https://shields.io" alt="RTL-SDR Raw IQ and DSP"></a>

- **Practical DSP & *Microwaves101*** · [`open gist`](https://github.com)<br>
  Learn FFTs by applying them to real radio captures; read *Microwaves101* on SWR, 50Ω impedance matching, and decibels when my antenna setup needs fixing.

<p align="center">•─────⋅ᓚᘏᗢ⋅──────────⋅ᓚᘏᗢ⋅──────────⋅ᓚᘏᗢ⋅─────•</p>


<!-- 
//  ## Starter Milestone READMEs

### `stage-0-linux-c/milestone-c-sniffer/README.md`
```markdown
# Milestone 0: Raw-Socket Packet Sniffer in C

## Objective
Build a zero-dependency Ethernet/IPv4/TCP/UDP packet sniffer in pure C on Linux using `AF_PACKET` raw sockets.

## Constraints & Tooling
- Compile strictly with `gcc -Wall -Wextra -Werror -O2`
- Zero external packet libraries (no `libpcap`)
- Verified leak-free with `valgrind` and traced with `strace`

## What Broke & What I Learned
- **Byte ordering:** Forgetting `ntohs()` on EtherType and port numbers.
- **Struct padding:** Using `__attribute__((packed))` so C structs map cleanly onto wire headers.
```

### `stage-1-bare-metal/milestone-router-teardown/README.md`
```markdown
# Milestone 1: Cheap Router UART & SPI Flash Teardown

## Target Hardware
- **Device:** [Brand / Model / Hardware Rev]
- **SoC:** [Chip markings]
- **Flash Chip:** [e.g., Winbond 25Q64 8MB SPI NOR]

## Checklist
- [ ] Identify GND, TX, RX, and VCC pads with a multimeter
- [ ] Solder header pins and capture boot logs via `minicom` (`115200 8N1`)
- [ ] Sniff SPI bus clock/data lines with logic analyzer
- [ ] Dump full flash image and extract filesystem with `binwalk`
```

### `stage-2-network-stack/milestone-packet-dissection/README.md`
```markdown
# Milestone 2: Linux `netns` Router & Hex Header Dissection

## Setup
- Two isolated network namespaces (`ns-client`, `ns-server`) bridged through a Linux router namespace (`ns-router`) running `ip route` and `nftables` NAT rules.

## Hex Breakdown (`capture.pcap`)
- **Ethernet Header (14 bytes):** Destination MAC, Source MAC, EtherType (`0x0800`)
- **IPv4 Header (20 bytes):** Version/IHL (`0x45`), TTL, Protocol (`0x06` TCP), Checksum, Src/Dst IP
- **TCP Header (20+ bytes):** Src/Dst Ports, Seq/Ack numbers, Flags (`SYN`, `SYN-ACK`, `ACK`), Window Size
```

### `stage-3-signals-rf/milestone-433mhz-decoder/README.md`
```markdown
# Milestone 3: 433.92 MHz OOK/ASK Decoder from Raw IQ

## Hardware & Capture Specs
- **Receiver:** RTL-SDR v3/v4
- **Center Frequency:** `433.92 MHz`
- **Sample Rate:** `2.048 MSPS`
- **Modulation:** On-Off Keying (OOK) / PWM

## Pipeline
1. Capture raw uint8 IQ samples with `rtl_sdr`
2. Compute magnitude \(\sqrt{I^2 + Q^2}\) and apply low-pass envelope detection
3. Threshold pulses into binary bits and decode device ID + sensor payload
```
--!>
