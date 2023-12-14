# DHCP-Snooping

<h2>Description</h2>
Configure DHCP server on R1 and DHCP Snooping on SW1 and SW2. Verify results.

<h2>Environments Used </h2>

- <b>Cisco Packet Tracer</b> (2.2.43) <br />

- <b>Cisco IOS C2900 Software Version 15.1(4)M5<br />

<h2>Diagram </h2>
<img src="https://i.imgur.com/NQwNt6w.png" height="80%" width="80%" />

<h2>Walk-through:</h2>
Configure R1 with DHCP server.<br />
R1(config)#ip dhcp excluded-address 192.168.1.1 192.168.1.9<br />
R1(config)#ip dhcp pool POOL1<br />
R1(dhcp-config)#network 192.168.1.0 255.255.255.0<br />
R1(dhcp-config)#default-router 192.168.1.1<br />
<img src="https://i.imgur.com/ErqJamv.png" height="80%" width="80%" /> <br />
<img src="https://i.imgur.com/dzIHs0b.png" height="80%" width="80%" /> <br />
<br />
<br />
Configure SW1 and SW2 with DHCP Snooping. <br />
SW1(config)#ip dhcp snooping<br />
SW1(config)#ip dhcp snooping vlan 1<br />
SW1(config)#no ip dhcp snooping information option<br />
SW1(config)#interface g0/2 (interface going towards DHCP Server)<br />
SW1(config-if)#ip dhcp snooping trust<br />
SW1(config-if)#do show run<br />
<img src="https://i.imgur.com/rSEStqG.png" height="80%" width="80%" /> <br />
<img src="https://i.imgur.com/DaQOf44.png" height="80%" width="80%" /> <br />
SW2(config)#ip dhcp snooping<br />
SW2(config)#ip dhcp snooping vlan 1<br />
SW2(config)#no ip dhcp snooping information option<br />
SW2(config)#interface range g0/1<br />
SW2(config-if)#ip dhcp snooping trust<br />
SW2(config-if-range)#do show run<br />
<img src="https://i.imgur.com/Trv5fuD.png" height="80%" width="80%" /> <br />
<img src="https://i.imgur.com/7rpFKnh.png" height="80%" width="80%" /> <br />
Verify Results.<br />
<img src="https://i.imgur.com/TjirdA1.png" height="80%" width="80%" /> <br />
<img src="https://i.imgur.com/yHteVBz.png" height="80%" width="80%" /> <br />


