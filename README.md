# implementation-of-6t-and-8t-Sram
# 6T SRAM
The conventional 6T memory cell comprised of two CMOS invertors cross coupled with two pass transistors connected to a complimentary bit lines as shown in Figure 1. The gate of access transistors N3 and N4 are connected to the WL (word line) to have data written to the memory cell or read from the memory cell through the BL or BLB (bitlines) during write and read operation.
The bit lines act as I/O buses which carry the data from the memory cell to the sense amplifier. Although it is not necessary to have two bit lines, both the signal and its inverse are typically provided in order to improve noise margins. SRAM cell perform three different operations, read, write and hold operation.

![image](https://user-images.githubusercontent.com/82768295/219868397-47786b81-11f9-47f8-81a6-d32105c6119f.png)

# Static Noise Margin
The stability of SRAM circuit depends on the Static Noise Margin. A basic SNM is obtained by drawing and mirroring the inverter characteristics and finding the maximum possible square between them. This is a graphical technique of estimating the SNM
![image](https://user-images.githubusercontent.com/82768295/219868433-8d85d752-3cba-4ffa-a91f-b1f0b298ea9b.png)


Figure 2 shows a common way of representing the SNM graphically for a bit-cell holding data. It plots the Voltage Transfer Characteristic (VTC) of Inverter 2 (inv2) and the inverse VTC-1 from Inverter 1(inv1). The resulting two-lobed curve is called a “butterfly curve” and is used to determine the SNM. The SNM is defined as the length of the side of the largest square that can be embedded inside the lobes of the butterfly curve.

Consider the case when the value of the noise sources with value Vn are introduced at each of the internal nodes in the bit cell. When the value of Vn increases from 0, this causes the VTC-1 for first inverter in Figure 2 to move downward and the VTC for the second inverter to move to the right. Once both move by the SNM value, the curves meet at only two points.
![image](https://user-images.githubusercontent.com/82768295/219868444-e9cc344a-0f2c-4423-9c23-8fdd703a2807.png)
The resulting two-lobed curve is called as a “butterfly curve” as shown in Figure 3 and is used to determine the SNM. Values of SNM vary in different operation mode. SNM is becoming important factor to check the stability during read operation. It’s visible in the Fig. 3 that during read operation, the SNM takes its lowest value and the cell is in its weakest state.
The SRAM cell immunity to static noise is measured in terms of SNM that quantifies the maximum amount of voltage noise that can be tolerated at the cross-inverters output nodes without flipping the cell [4]. Any change in the noise, changes the value of the SNM during cell operation. Though the SNM is important during hold, cell stability during active operation represents a more significant limitation to SRAM operation

# Stability Problem in 6T SRAM
The conventional 6T-cell schematic is shown in Figure 4. This most commonly used SRAM cell implementation has the advantage of very less area [5].
However, the potential stability problem of this design arises during read and writes operation, where the cell is most vulnerable towards noise and thus the stability of the cell is affected. If the cell structure is not designed properly, it may change its state during read and write operation. There are two types of noise margin which affects the Cell stability that are discussed shortly.

![image](https://user-images.githubusercontent.com/82768295/219868526-a2886a63-e43b-48db-b181-da09d289b752.png)


Read Static Noise Margin
#
During read accesses, the Read-SNM decreases [8]. This is due to the reason that Read-SNM is calculated when the word line is set high and both bit line are still precharged high. At the onset of a read access, the access transistor (WL) is set to “1” and the bit-lines are already precharged to “1”.The internal node of the bit-cell representing a zero gets pulled upward through the access transistor due to the voltage dividing effect across the access transistor and drive transistor. This increase in voltage severely degrades the SNM during the read operation as shown in the Figure 3.
During the read operation, a stored “0” can be overwritten by a “1” when the voltage at node V1 reaches the Vth of nMOS N1 to pull node V2 down to “0” and in turn pull node V1 up even further to “1” due to the mechanism of positive feedback. This results in wrong data being read or a destructive read when the cell changes state [7].
#


Write Static Noise Margin

The write noise margin is defined as the minimum bitline voltage needed to flip the state of cell. During a write operation, the input data are sent to the bitlines, and then the word lines are activated to access the cell. The bitline that is charged to ‘0’ pulls the node of the cell storing ‘1’ to ‘0’ causing the cell to flip state. Since the cross-coupled inverters have complementary data, their VTCs are measured using different circuits. The circuit that represents the inverter with ‘1’ at its output and its bitline is connected to GND to simulate a write ‘0’ to that node. A DC voltage sweep is applied at node V1 and the voltage output at node V2 is measured, when the bitline( BL) is connected to GND and wordline (WL) is charged to Vdd.

# 8T SRAM
It is noteworthy that for associate SRAM cell, the specified form of operation is commonly set with the correct choice of the bit line voltage. However, this involves additional edge circuits like bit line precharge circuits and writes drivers to create positive correct bit line voltage setting before any operation. At low provide voltages due the soundness limitations of 6T SRAM cell we tend to use 8T SRAM cell for quick transmission applications. it's like 6T SRAM cell with a scan decoupled path that consists of M5 and M6 transistors. Allow us to see the operating of 8T SRAM style.

![image](https://user-images.githubusercontent.com/82768295/219868742-068b7db0-7de1-4eb1-9a27-0f7fda444137.png)


# Write Operation
#
Write ‘1’ Operation
Likewise writing ‘1’ is also carried in the likely same. The bit line has to give a value VDD and bit line bar is given a value 0 volts. As WWL is enabled for write operation, the values in bit lines are store at respective nodes that is at Q will have value logical ‘1’ and logical ‘0’ at Qbar. There is no change in the write operation when compared with the basic SRAM operation.

#
Write ‘0’ Operation
For writing ‘0’, the bit line has to give zero volts and VDD to the bit line (BLbar). And write word line is asserted which makes both the transistors M3 and M4 ON. Hence the value in the bit line is stored at Q. Hence ‘0’ is stored at Q.

# Read Operation
#
Read ‘0’ Operation

Read word line (RWL) drives the access transistor M5 ON. If the value stored at Q is ‘0’ then transistor M6 will be ON and RBL is connected to ground directly through M5&M6 transistors discharges. This implies that the value stored at Q in the SRAM is zero.
#
Read ‘1’ Operation
If the value stored at Q is ‘1’, due to M6 transistor will be OFF and there is no discharge path for RBL, and the value in RBL is VDD which shows that value stored at Q is ‘1’. The circuit diagram of 8T SRAM shown in the figure 4.
The disadvantages in 6T SRAM are minimized in 8T SRAM, even though the transistor count increased the power consumption. The circuit diagram and operations of conventional and 8T SRAM are discussed in this chapter. The SRAM with charge sharing concept is discussed next.


# CHECK RESULTS IN THEIR RESPECTIVE FOLDERS


