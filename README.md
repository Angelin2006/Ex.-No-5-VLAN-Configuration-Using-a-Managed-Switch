## Ex. No: 5  VLAN Configuration Using a Managed Switch
Date:29/10/26
________________________________________
# Objective
To configure Virtual Local Area Networks (VLANs) on a managed switch and verify that hosts within the same VLAN can communicate while others cannot.
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Managed Switch (e.g., 2960)<br>
•	4 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram

<img width="1366" height="768" alt="Screenshot 2026-10-29 154632" src="https://github.com/user-attachments/assets/4cfe5642-90d8-4b11-b756-bbf4160c4859" />

Description:<br>
•	PC0 and PC1 are assigned to VLAN 10.<br>
•	PC2 and PC3 are assigned to VLAN 20.<br>
•	All PCs are connected to different ports on the same switch.<br>

________________________________________
# IP Addressing Table
Device	VLAN	IP Address	Subnet Mask	Port<br>
PC0	10	192.168.10.1	255.255.255.0	FastEthernet0/1<br>
PC1	10	192.168.10.2	255.255.255.0	FastEthernet0/2<br>
PC2	20	192.168.20.1	255.255.255.0	FastEthernet0/3<br>
PC3	20	192.168.20.2	255.255.255.0	FastEthernet0/4<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 4 PCs and 1 Switch.<br>
2.	Connect PC0–PC3 to switch ports FastEthernet0/1 to FastEthernet0/4 respectively.<br>
3.	Assign static IP addresses to each PC as per the IP table.<br>
4.	Enter the Switch CLI and create two VLANs:<br>
o	VLAN 10 for PC0 and PC1<br>
o	VLAN 20 for PC2 and PC3<br>
5.	Assign the respective switch ports to their VLANs.<br>
6.	Use the ping command from PC0 to PC1 (should succeed).<br>
7.	Try pinging from PC0 to PC2 (should fail — different VLANs).<br>
________________________________________
# Commands Used (Switch CLI)
bash<br>
CopyEdit<br>
Switch> enable<br>
Switch# configure terminal<br>

Switch(config)# vlan 10<br>
Switch(config-vlan)# name STAFF<br>
Switch(config-vlan)# exit<br>

Switch(config)# vlan 20<br>
Switch(config-vlan)# name STUDENTS<br>
Switch(config-vlan)# exit<br>

Switch(config)# interface range fastethernet0/1 - 2<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 10<br>
Switch(config-if-range)# exit<br>

Switch(config)# interface range fastethernet0/3 - 4<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 20<br>
Switch(config-if-range)# exit<br>

<img width="1366" height="767" alt="Screenshot 2026-10-29 154824" src="https://github.com/user-attachments/assets/b989e6a0-2643-4b35-a582-b077940dd52b" />

________________________________________
# Output (Screenshots)
<img width="1361" height="767" alt="Screenshot 2026-10-29 154708" src="https://github.com/user-attachments/assets/e55c2dc0-21e6-4365-beac-f9d0e0ebea72" />
<img width="1366" height="768" alt="Screenshot 2026-10-29 154650" src="https://github.com/user-attachments/assets/25de10f4-7c5a-4b98-a60e-36b7dd5a8d33" />
<img width="1366" height="768" alt="Screenshot 2026-10-29 154729" src="https://github.com/user-attachments/assets/8e693e55-28df-412a-b03b-ab4ecb0411bf" />
<img width="1366" height="768" alt="Screenshot 2026-10-29 154751" src="https://github.com/user-attachments/assets/5664e244-cfd8-4025-9a47-d82a4b50afa0" />
<img width="1366" height="768" alt="Screenshot 2026-10-29 154800" src="https://github.com/user-attachments/assets/b371fc7d-d0f2-44b3-be47-c1aecb131274" />
<img width="1366" height="768" alt="Screenshot 2026-10-29 154838" src="https://github.com/user-attachments/assets/13b0bc47-0248-45bb-8bcd-dce70b8d6e7b" />

________________________________________
# Result
Successfully created and configured VLANs on a managed switch. Verified that only PCs within the same VLAN could communicate with each other.

