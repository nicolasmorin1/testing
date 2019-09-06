*************
Introduction 
*************

This document describes the Reference Firmware for the Programmable Logic (PL) on the VP430. This design flow is based on the Xilinx Vivado IP Integrator (IPI) flow using Vivado 2018.2.1. A description of the Vivado IPI flow is beyond the scope of this document, but can be found in the Xilinx User Guide UG994: Designing IP Subsystems Using IP Integrator. This document only gives a global description of each custom IP included in the design. Detailed information can be found in the Star Document (SD###) available for each custom IP.

Reference Firmware Architecture 
################################

The VP430 is Abaco Systems’ 3U OpenVPX payload module that employs Xilinx’s Zynq UltraScale+ Radio Frequency System on Chip (RFSoC) device to provide high-speed, low-latency, Digital-to-Analog and Analog-to-Digital conversion. The Reference Firmware for the PL on the VP430 is architected to provide a reference for getting started with all of the interfaces that are exposed on the VP430 through the PL on the RFSoC device.

The RFSoC device is a combination of embedded micro-processors, FPGA fabric, and RF Converters. Due to the way that Xilinx integrates all of this functionality into the Vivado, SDK, and PetaLinux tools, the VP430 Reference Firmware is designed entirely inside of a Vivado IPI Block Design. It is a combination of standard IP cores from the Xilinx IP Catalog installed along with Vivado and custom IP cores designed by Abaco Systems to meet the requirements of the VP430 Reference Firmware.

The top-level block diagram for the VP430 Reference Firmware architecture can be seen in Figure 1 below:

.. image:: https://github.com/nicolasmorin1/testing/blob/master/images/vp430_block_diagram.png

Vivado IPI Block Design Description 
#####################################

Several sections of the design are wrapped inside of hierarchical blocks, or sub-blocks, to make the Vivado IPI Block Design easier to view and easier to understand. This section will start at the top level of the Block Design, then expand into each sub-block in order to provide a brief description of each of the IP cores included in the design.

Top-Level Block Design Description 
************************************

The top-level of the VP430 Vivado IPI Block Design is depicted in Figure 2 below. It has the following IP cores:

1. VP430 info  
2. VP430 8-Lane PCIe  
3. VP430 DDR4 FIFO  
4. AXI Interconnect  
5. AXI4-Stream Interconnect  
6. AXI I2C Master  

.. image:: https://github.com/nicolasmorin1/testing/blob/master/images/vp430_ip_integrator.png 

VP430 Info 
**************

The VP430 Info IP core holds information about the design (design ID, design revision, etc.). Please refer to SD526 for more information on the VP430 Info IP.

VP430 8-Lane PCIe
************************************

The VP430 8-Lane PCIe IP core distributes register read and register write commands coming from the PCIe interface on the VPX backplane. In addition, it also transfers DMA data to/from the host PC through the PCIe interface. Please refer to SD527 for more information on the VP430 8-Lane PCIe IP.

VP430 DDR4 FIFO
************************************

The VP430 DDR4 FIFO IP core acts as two separate FIFO buffers, each with 2GB of storage. All of the data is stored in the external DDR4 memory in blocks of configurable size. Buffer data is made available on the AXI4-Stream Master ports after one or more blocks are available in the external memory. Please refer to SD524 for more information on the VP430 DDR4 FIFO IP.



