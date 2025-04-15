# Geo Location Threat Monitoring


<h2>Description</h2>
This project sets up a honeypot in Microsoft Azure by deploying a virtual machine (VM) intentionally exposed to the public internet. The goal is to attract real-world cyberattacks within minutes or hours of deployment, allowing us to observe and analyze attacker behavior in a controlled environment.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Kusto Query Language (KQL)</b><br/>
- <b>Microsoft Sentinel</b><br/>
- <b>Azure Log Analytics</b><br/>
- <b>PowerShell</b><br/>
- <b>Windows Event Logs</b>


<h2>Project Setup Diagram</h2>
<img src="https://i.imgur.com/6egLgA2.png" height="80%" width="80%" alt=""/>


<h2>Program walk-through:</h2>

<h3>Create a Resource Group</h3> <br/>

<img src="https://i.imgur.com/pzbczW0.png" height="80%" width="80%" alt=""/>
<br />

<h3>Create a Virtual Network</h3> <br/>

<img src="https://i.imgur.com/JM1uJeM.png" height="80%" width="80%" alt=""/>
<br />

<h3>Create a VM</h3> <br/>

<img src="https://i.imgur.com/jACM5V6.png" height="80%" width="80%" alt=""/>
<br />

<h3>Adding an inbound security rule to the Network Security Group to allow any type of traffic into the VM</h3> <br/>

<img src="https://i.imgur.com/4xG2jfU.png" height="80%" width="80%" alt=""/>
<br />

<h3>Created a Remote Desktop Connection to turn of the firewall in the VM</h3> <br/>

<img src="https://i.imgur.com/C1P1lcR.png" height="80%" width="80%" alt=""/>
<br />


<h3>Creating a Log Analytics Workspace </h3> <br/>

<img src="https://i.imgur.com/9xdvRNM.png" height="80%" width="80%" alt=""/>
<br />


<h3>Connecting our log workspace to the siem to access the logs from our log repository from our siem </h3> <br/>

<img src="https://i.imgur.com/N0MltF3.png" height="80%" width="80%" alt=""/>
<br />

<h3>Now we’ll connect the log workspace to the VM by installing the Security Events Connector in Sentinel. This means that we’re going to connect the log repository to the VM to observe them</h3> <br/>

<img src="https://i.imgur.com/9wzzZlH.png" height="80%" width="80%" alt=""/>
<br />

<h3>Installing Windows Security Events monitoring</h3> <br/>

<img src="https://i.imgur.com/2ZUJLqJ.png" height="80%" width="80%" alt=""/>
<br />

<h3>We’re going to create the Windows Security Events via AMA . It is used by the VM to forward logs to the logs workspace which we can then access via our SIEM</h3> <br/>

<img src="https://i.imgur.com/yv9tN71.png" height="80%" width="80%" alt=""/>
<br />

<h3>Here we can see that the logs of failed attempts by hackers</h3> <br/>

<img src="https://i.imgur.com/AhD0k8z.png" height="80%" width="80%" alt=""/>
<br />

<h3>The SecurityEvent logs in the Log Analytics Workspace do not include geographic location data by default—only the source IP addresses. To enrich this data and determine where attacks are coming from, we import a spreadsheet into Microsoft Sentinel as a watchlist. This spreadsheet contains geographic information mapped to IP address ranges. Once the watchlist is created and fully imported—consisting of approximately 54,000 rows, Sentinel can correlate the IP addresses in the logs with the location data from the watchlist.</h3> <br/>

<img src="https://i.imgur.com/mbFpZQG.png" height="80%" width="80%" alt=""/>
<br />

<h3></h3> <br/>

<img src="https://i.imgur.com/mbAfGrD.png" height="80%" width="80%" alt=""/>
<br />

<h3>Creating a workbook to visualize the attack</h3> <br/>

<img src="https://i.imgur.com/Qwik1rm.png" height="80%" width="80%" alt=""/>
<br />

<h3>World map of incoming attacks after 24 hours</h3> <br/>

<img src="https://i.imgur.com/RE3pWKh.png" height="80%" width="80%" alt=""/>
<br />

<h2>Final Thoughts</h2>
<p>
    This project gave me hands-on experience with deploying and monitoring a honeypot environment in Microsoft Azure. It provided valuable insight into real-world cyberattacks and demonstrated how to collect, forward, and analyze logs using Microsoft Sentinel. Setting up the attack map using enriched IP data helped visualize threats geographically, offering a clearer understanding of global attack patterns. This project not only strengthened my knowledge of cloud-based security monitoring but also improved my skills with KQL, SIEM tools, and log analysis.
</p>

<h3>Skills Gained:</h3>
<ul>
    <li>Cloud Security Monitoring (Microsoft Sentinel, Azure)</li>
    <li>Log Analytics & SIEM Integration</li>
    <li>Data Enrichment with Watchlists</li>
    <li>KQL (Kusto Query Language) for querying and visualizations</li>
    <li>Threat Visualization with Workbooks and Geo Maps</li>
</ul>


