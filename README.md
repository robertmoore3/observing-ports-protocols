

<h1>Observing Ports and Protocals</h1>
This tutorial is designed to build intuition for various network protocals.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- WireShark

<h2>Operating Systems Used </h2>

- Windows 10
- Linux


<h2>Create our Virtual Machines (VM) </h2>
<ul>
  <li>We’ll be using a Windows 10 VM and a Linux (Ubuntu) VM.</li>
  <li>These VMs should be in the same Resource Group with the same Virtual Network and Subnet.</li>
</ul>
<br />

<h2>Observe ICMP Traffic</h2>
<p>
<img src="https://github.com/user-attachments/assets/05950454-0b2e-4859-808e-8e1728e51600"/>
</p>
<p>ICMP (Internet Control Message Protocol) is a network layer protocol used primarily for sending error messages and operational imformation between network devices.</p>
<ol>
  <li>Use Remote Desktop to connect to the Windows VM.</li>
  <li>Within the VM, install <a href='https://www.wireshark.org'>WireShark</a>.</li>
  <li>Open Wireshark and start packet capture. filter for icmp traffic only</li>
  (once you've opened WireShark, click the shark fin icon in the top left, beneath the 'file' button.)
  <li>Ping the linux vm’s private ip address</li>
  <li>Observe the requests and replies within WireShark</li>
  <li>Ping a public website (like www.google.com) and observe the traffic</li>
</ol>
<br />

<h2>Configuring a Firewall (Network Security Group in Azure)</h2>
<p>
<img src="https://github.com/user-attachments/assets/0c071077-5de1-4341-9c00-9b53b9f26ec3"/>
</p>
<ol>
  <li>Start a perpetual ping (using ping -t) from your Windows 10 VM to the Linux VM.</li>
  <li>In the Linxu VM’s Network Security Group, disable inbound ICMP traffic.</li>
  linux-vm → network settings → create port rule → inbound port rule → set protocol to ICMPv4 and Action to Deny
  <li>Observe ICMP traffic in WireShark and the command line ping output.</li>
  <li>Re-enable ICMP traffic and verify ping resumes.</li>
  <li>Stop the ping activity by pressing Control + C in the terminal window</li>
</ol>
<br />

<h2>Observing SSH Traffic</h2>
<p>
<img src="https://github.com/user-attachments/assets/c1812d57-c1a1-4fdb-90be-39d2c8bbf6b0"/>
</p>
<p>SSH (Secure Shell) is a network protocol that allows secure remote access and management of devices over an encrypted connection.</p>
<ol>
  <li>Open Wireshark and filter for SSH traffic.</li>
  <li>SSH into the Ubuntu VM using PowerShell: ssh labuser@<private IP>.</li>
  <li>Enter login credentials and observe SSH traffic in Wireshark.</li>
  <li>Exit the SSH session.</li>
</ol>
<br />

<h2>Observing DHCP Traffic</h2>
<p>
<img src="https://github.com/user-attachments/assets/593eb18e-18fd-4f8c-a804-84e2e97ff421"/>
</p>
<p>DHCP (Dynamic Host Configuration Protocol) is a network management protocol used to automatically assign IP addresses and other network settings to devices on a network. </p>
<ol>
  <li>Filter Wireshark for DHCP traffic.</li>
  <li>In PowerShell (as an admin), renew the IP address: ipconfig /renew.</li>
  <li>Observe DHCP traffic in Wireshark.</li>
</ol>
<br />

<h2>Observing DNS</h2>
<p>
<img src="https://github.com/user-attachments/assets/e563730f-45a9-48d5-ac5c-2601e71df8df"/>
</p>
<p>DNS (Domain Name System) is a protocol that translates human-readable domain names into IP addresses.</p>
<ol>
  <li>Filter Wireshark for DNS traffic.</li>
  <li>Use nslookup to query google.com and disney.com.</li>
  <li>Observe DNS traffic in Wireshark.</li>
</ol>
<br />

<h2>Observing RDP Traffic</h2>
<p>
<img src="https://github.com/user-attachments/assets/62025c94-fe19-4076-9b39-33c72aaabef7"/>
</p>
<p>RDP (Remote Desktop Protocol) allows users to remotely access and control another computer over a network. </p>
<ol>
  <li>Filter Wireshark for RDP traffic (tcp.port == 3389).</li>
  <li>Observe continuous traffic due to RDP’s live data stream.</li>
</ol>
<br />



