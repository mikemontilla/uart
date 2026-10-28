# UART Interface Implementation

This project implements the well-known UART communication protocol on an FPGA, both as a way to learn the protocol and to showcase a possible implementation on a Lattice FPGA. Development is split into the following stages:

1. **Stage 1:** Send a single character over the serial port every second, to be displayed in a terminal on the computer.
2. **Stage 2:** Send a full word (`"Hello\n"`) every second, to be displayed in a terminal on the computer.
3. **Stage 3:** Receive any word from the computer's terminal and reply by prepending `"Hello "` to it. The terminal should display `"Hello "` + the received word.

## Tools and Hardware

| Item                    | Details                                                                                                              |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------- |
| Board                   | TD112 (developed by Tachysséma Développement), an FPGA module mounted on a carrier board with peripherals and Pmod connectors |
| FPGA                    | Lattice Semiconductor CrossLink-NX LIFCL-40-8BG256I                                                                  |
| Toolchain               | Lattice Radiant 2026.1                                                                                               |
| Synthesis               | Synopsys Synplify Pro                                                                                                |
| Language                | VHDL-2008                                                                                                            |
| Programmer              | Radiant Programmer                                                                                                   |
| Diagrams                | draw.io                                                                                                              |
| Serial terminal         | picocom                                                                                                              |
| Operating system        | Ubuntu 22.04                                                                                                         |

## Stage 1: Sending One Byte per Second

### Specifications

- Send the ASCII character `U` (`0x55` = `0b01010101`) once per second.
- The character must appear in the picocom terminal every second.
- The character is sent continuously from system startup (no button press required).

## Notes

As in any project, big or small, development is a chance to learn new concepts or revisit old ones. The [NOTES.md](NOTES.md) file records some of the lessons learned along the way for future reference.
