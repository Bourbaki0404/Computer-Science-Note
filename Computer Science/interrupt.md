# PLIC

![](/interrupt/PLIC.jpg)

PLIC Architecture Bloack Diagram

# Useful Tips:
### Interrupt Target
- <span style="color:green">Interrupt targets</span> are usually hart contexts, where a hart context is a given privilege mode on a given hart (though there are other possible interrupt targets, such as DMA engines). 
### Gateway
- The <span style="color:green">interrupt gateways</span> are responsible for converting global interrupt signals into a common interrupt request format, and for controlling the flow of interrupt requests to the PLIC core. At most one interrupt request <span style="color:yellow"> per interrupt source</span> can be pending<span style="color:cyan"> in the PLIC core</span> at any time, indicated by setting the source’s IP bit. 

The gateway only forwards a new interrupt request to the PLIC core after receiving <u>notification</u> that the interrupt handler servicing the previous interrupt request from the same source has completed.

The gateway does not have the facility to retract an interrupt request once forwarded to the PLIC core.
### Interrupt Notification
- Each interrupt target has an<span style="color:yellow"> external interrupt pending (EIP) bit </span> in the PLIC core that indicates that the corresponding target has a pending interrupt waiting for service. The value in EIP can change as a result of changes to state in the PLIC core, brought on by interrupt sources, interrupt targets, or other agents manipulating register values in the PLIC. The value in EIP is communicated to the destination target as an interrupt notification. <span style="color:cyan">If the target is a RISC-V hart context, the interrupt notifications arrive on the meip/seip bits depending on the privilege level of the hart context</span>.

- Interrupt Pending Bits registers:
The interrupt pending status of each <span style="color:yellow">interrupt source.</span>