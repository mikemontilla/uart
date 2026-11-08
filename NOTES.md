# Study Notes

This document records the lessons learned while developing this project: short notes on concepts and procedures I can come back to later as a refresher.

## UART

At first I didn't quite understand how the data frame would tell the receiver how many data bits were being sent, whether there was a parity bit, or how many stop bits there were. It turns out all of this is agreed upon (that is, configured) between the communicating devices before any transmission takes place.

As for the stop bit, it exists precisely so that, when several bytes are sent back to back, it is possible to tell where one ends and the next begins. In other words, it guarantees there is always a clean falling edge into the start bit that marks the beginning of the next byte.

## How the Shift Register Works

For the shift register, which converts parallel data into serial data, I initially thought it could simply shift out whatever was present at its input at any given moment. That approach is fragile, because the data could change in the middle of the operation and garbage would be sent. A load function is needed: one that takes a snapshot of the parallel data so it can then be sent out one bit at a time. Whether the register is loading or shifting on each clock cycle can be controlled through a mode set by the state machine.

## Moore and Mealy State Machines

In this design I learned that, in order to use fewer states, it is important to be able to mix the Moore and Mealy state machine concepts. In a Moore machine, the outputs depend only on the current state, whereas in a Mealy machine they depend on both the current state and the system inputs. This makes it possible to set certain outputs right at the moment of the transition from one state to another.

## ASM Charts

ASM (Algorithmic State Machine) charts are a way to design a state machine that can combine Moore and Mealy outputs in a single chart, showing its behavior as an algorithm. They are somewhat more complex and are usually best suited to designs that need to represent decisions or complex outputs in greater detail. In this project, an ASM chart is used only as practice, to describe the machine that controls the different states of the UART communication. Some examples can be found in the implementation documents.
