<h1>NAT: Netowrk Address Translation</h1>

<h2>Description</h2>
In this lab, Network Address Translation will be configured for a small Enterprise. NAT can configured using static NAT, dynamic NAT and PAT. In this lab static NAT and PAT will be used.
<br />

<h2>Environments Used </h2>

- <b>Packet Tracer</b>

<h2>Lab walk-through:</h2>

<p align="center">
<h4>Lab Topology:</h4>
In this lab there are 2 networks, the "INSIDE NETWORK" and the "OUTSIDE NETWORK", the goal is to make the "INSIDE NETWORK" communcate with the "OUTSIDE NETWORK", with the "INSIDE NETWORK" using private addressing translated by NAT.<br/><br/>

The routers, servers and PCs have been configured with their internal address settings.<br/>
"INSIDE ROUTER" is the WAN edge router of the "INSIDE NETWORK". It has a default route pointing to the Service Provider router "SERVICE PROVIDER ROUTER" <br/><br/>
The "INSIDE NETWORK" has bought the range of public addreses 220.0.0.0/28
220.0.0.1 has been assigned to "INSIDE ROUTER" g0/0 interface <br/>
220.0.0.2 has been assigned to "SERIVE PROVIDER ROUTER" g0/0 interface <br/>
220.0.0.3 - 220.0.0.14 are the remaining available public ip addresses that can be used.<br/>
<img src="https://i.imgur.com/UX8Uj4X.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<h4>Outside and Inside Interfaces:</h4> 
Before NAT is configured, all interfaces on the "INSIDE ROUTER" pointing to the "INSIDE NETWORK" need to be labled as NAT inside, and all the interface pointing to the "OUTSIDE NETWORK", need ot be labled as NAT outisde. <br/>
<img src="https://i.imgur.com/zi3YGx3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
<h4>Static NAT: </h4>
INSIDE SERVER is a web server. It must accept incoming connections from the outside. It must have a static NAT configuretion <br/>
The INSIDE SERVER at 10.10.10.10 was statically mapped to public IP Adreess 220.0.0.3<br/>
<img src="https://i.imgur.com/lduCwRL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
The INSIDE SERVER can now ping the OUTSIDE SERVER at 180.0.0.3 and as can be seen from the NAT translation table the private address 10.10.10.10 was translated to 220.0.0.3  <br/>
<img src="https://i.imgur.com/zpvvKwI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br/>
<img src="https://i.imgur.com/1U8YA7L.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
<h4>PAT:</h4>
"SUBNET 10.10.20.0" will use the address of the "INSIDE ROUTER"'s g0/0 interface to communicate with the "OUTSIDE NETWORK".<br/>
All of the addresses in the 10.10.20.0 subnet will use one address.<br/>
To do this, an access list is create to permit the 10.10.20.0 subnet and NAT is enabled for the sunet using the g0/0 interface.<br/>
<img src="https://i.imgur.com/YFyHZso.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/iNUcc2D.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
The 10.10.20.0 subnet can now ping the "OUTSIDE SERVER" on 180.0.0.3 and as can be seen from the NAT translation table all of the adresses were translated to 220.0.0.1 <br/>
<img src="https://i.imgur.com/RTUlGrH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/dIEzR5d.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/bgCffUq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


@@ text in purple (and bold)@@
```
--!>
