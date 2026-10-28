# Study Notes

This document records the lessons learned while developing this project: short notes on concepts and procedures I can come back to later as a refresher.

## UART

At first I didn't quite understand how the data frame would tell the receiver how many data bits were being sent, whether there was a parity bit, or how many stop bits there were. It turns out all of this is agreed upon (that is, configured) between the communicating devices before any transmission takes place.

As for the stop bit, it exists precisely so that, when several bytes are sent back to back, it is possible to tell where one ends and the next begins. In other words, it guarantees there is always a clean falling edge into the start bit that marks the beginning of the next byte.
