<h1>Configuring Port Address Translation</h1>


<h2>Description</h2>
In this lab, I learned to configure PAT. PAT (Port Address Translation) is a variant of NAT (Network Address Translation) in which multiple inside local IP addresses share a single inside global IP address. PAT can distinguish between different flows based on port numbers.
<br />



<h2>Environments Used </h2>

- <b>Ubuntu 20.04.2 LTS</b> 
- <b>PuTTY SSH Client</b>

<h2>Program walk-through:</h2>

<p align="center">
From the left sidebar click PuTTY SSH Client and proceed to put in the private IP address, port number, click Telnet and then click open.: <br/>
<img src="https://i.postimg.cc/z3mdx877/Screen-Shot-2022-08-10-at-4-21-00-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />
  
  
<br />
In the R4 terminal window execute the following one line at a time to enter into configuration mode and configure NAT and enable natting on interfaces for network translation :  <br/>
1.configure terminal<br/>
2. access-list 1 permit 192.168.1.0 0.0.0.255<br/>
3. ip nat pool uc 192.168.3.50 192.168.3.50 netmask 255.255.255.0<br/>
4. ip nat inside source list 1 pool uc overload<br/>
5. int e0/1<br/>
6. ip nat inside <br/>
7. int e0/0 <br/>
8. ip nat outside <br/>
9. end <br/>
<img src="https://i.postimg.cc/vZx0p1kz/Screen-Shot-2022-08-10-at-4-29-42-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />
  
  
  
<br />
 Go to the side bar and select a new PuTTY SSH Clinet window and enter in IP address, Port, and connection type and click open<br/>
<img src="https://i.postimg.cc/9z5D0nXz/Screen-Shot-2022-08-10-at-4-34-57-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
 
  
  
  
<br />
In the P2 window use comand ping to observe the connectivity of the IP address<br/>
<img src="https://i.postimg.cc/mDTDvHX1/Screen-Shot-2022-08-10-at-4-39-00-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />
  
  
  
<br />
In the R4 terminal type command: show ip nat translations. This command displays the active NAT :  <br/>
<img src="https://i.postimg.cc/k5LZG0Rx/Screen-Shot-2022-08-10-at-4-50-36-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />
  
  
  

  

  
  
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
