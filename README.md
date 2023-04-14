# APB-Protocol
## Introduction
The APB is part of the AMBA 3 protocol family. It provides a low-cost interface that is 
optimized for minimal power consumption and reduced interface complexity.
The APB interfaces to any peripherals that are low-bandwidth and do not require the 
high performance of a pipelined bus interface. The APB has unpipelined protocol.
All signal transitions are only related to the rising edge of the clock to enable the 
integration of APB peripherals easily into any design flow. Every transfer takes at least 
two cycles.
The APB can interface with the AMBA Advanced High-performance Bus Lite
(AHB-Lite) and AMBA Advanced Extensible Interface (AXI). You can use it to provide 
access to the programmable control registers of peripheral devices.
##  Operating states
![1](https://user-images.githubusercontent.com/65547096/232087447-18f8c4b6-7a3a-4617-aca0-d6e567ed35ce.PNG) <br>
The state machine operates through the following states:
* IDLE This is the default state of the APB.
* SETUP When a transfer is required the bus moves into the SETUP state, where 
the appropriate select signal, PSELx, is asserted. The bus only remains 
in the SETUP state for one clock cycle and always moves to the ACCESS 
state on the next rising edge of the clock.
- ACCESS The enable signal, PENABLE, is asserted in the ACCESS state. The 
address, write, select, and write data signals must remain stable during 
the transition from the SETUP to ACCESS state.
Exit from the ACCESS state is controlled by the PREADY signal from 
the slave:
  * If PREADY is held LOW by the slave then the peripheral bus 
remains in the ACCESS state
  * If PREADY is driven HIGH by the slave then the ACCESS state is 
exited and the bus returns to the IDLE state if no more transfers are 
required. Alternatively, the bus moves directly to the SETUP state 
if another transfer follows.
## Master-Slave Interface
![4](https://user-images.githubusercontent.com/65547096/232092989-7c287fb6-9077-497b-8702-601d957174a7.PNG)

