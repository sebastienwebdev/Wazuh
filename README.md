<h1>Wazuh Intrusion Detection System (IDS)</h1>

 ### [Medium Article Demonstration](https://medium.com/@sebastienwebdev/deploying-a-wazuh-intrusion-detection-system-on-linode-and-azure-59a7dbc16ac1)

<h2>Description</h2>
This project guides you through deploying a Wazuh Intrusion Detection System (IDS) on Linode and setting up a honeypot on Azure, offering a comprehensive learning experience in cybersecurity. Wazuh, an open-source platform for security monitoring, intrusion detection, and compliance, is utilized for its scalability and adaptability across different environments. By setting up Wazuh Manager on Linode, you'll delve into configuring and monitoring security events, while Azure facilitates the creation of a honeypot to attract and analyze cyber attacks. The project involves detailed steps for adding agents across various operating systems, including MacOS, Windows, and Ubuntu, to monitor system activities and detect vulnerabilities. Through practical exercises like installing outdated software on the honeypot and analyzing security events through Wazuh's dashboard, you'll gain insights into threat detection and incident response. This project not only sharpens your cybersecurity skills but also prepares you for roles in security analysis, demonstrating your capability to implement and manage advanced security solutions.
<br />

<h2>Environments & Utilies Used </h2>

- <b>Windows 10,Ubuntu,macOS</b> 
- <b>Linode & Azure</b>
- <b>Virtual environment software (Parallel, Virtualbox, Vmware, etc...)</b>
- <b>Outdated Program </b>

<h2>Program walk-through:</h2>

<p align="center">
Setup Linode: <br/>
<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*X78nKhLxRL4qFSK6aLsXEg.png" height="80%" width="80%" alt="Linode Setup Steps"/>
<br />
<br />
<h2>Adding Agents:</h2>

<h3>macOS</h3>
<p><strong>Install the Agent:</strong> Use the shell command to download and install the Wazuh agent on your macOS.</p>
<pre><code>curl -L -O https://packages.wazuh.com/4.x/macos/wazuh-agent-4.7.3-1.arm64.pkg</code></pre>

<p><strong>Configure the Agent:</strong> Edit the <code>ossec.conf</code> file located at <code>/Library/Ossec/etc/ossec.conf</code>. Set the manager IP to your Linode's reverse DNS domain, and specify the group your agent belongs to.</p>

<p><strong>Manage the Agent Service:</strong> Use <code>launchctl</code> to unload and load the Wazuh agent service, applying your configuration changes.</p>

<h3>Windows</h3>
<p><strong>Open PowerShell:</strong> Right-click the Start button, select “Windows PowerShell (Admin)” to open PowerShell with administrative privileges.</p>

<p><strong>Download the Installer:</strong> Copy and paste the following command into PowerShell. This command downloads the Wazuh agent installer to your system.</p>
<pre><code>Invoke-WebRequest -Uri "https://packages.wazuh.com/4.x/windows/wazuh-agent-4.7.3-1.msi" -OutFile "${env:TEMP}\wazuh-agent-4.7.3-1.msi"</code></pre>

<p><strong>Execute the Installer:</strong> Still in PowerShell, execute the following command to install the Wazuh agent. Replace YOUR_MANAGER_IP with the IP address of your Wazuh manager (Inverse DNS of your Linode)</p>
<pre><code>msiexec.exe /i "${env:TEMP}\wazuh-agent-4.7.3-1.msi" /q WAZUH_MANAGER="YOUR_MANAGER_IP" WAZUH_AGENT_GROUP="default" WAZUH_REGISTRATION_SERVER="YOUR_MANAGER_IP"</code></pre>

<h3>Ubuntu Systems</h3>
<p><strong>Open Terminal:</strong> You can find the Terminal application in your applications menu, or press Ctrl+Alt+T to open it.</p>

<p><strong>Download and Install the Agent:</strong> Copy and paste the following command into the Terminal. This will download and install the Wazuh agent on your Ubuntu system. Remember to replace YOUR_MANAGER_IP with the IP address of your Wazuh manager.</p>
<pre><code>wget https://packages.wazuh.com/4.x/apt/pool/main/w/wazuh-agent/wazuh-agent_4.7.3-1_arm64.deb && sudo dpkg -i ./wazuh-agent_4.7.3-1_arm64.deb</code></pre>

<p><strong>Edit the Configuration File:</strong> The configuration file is located at <code>/var/ossec/etc/ossec.conf</code>. Open it with a text editor such as Nano. For example:</p>
<pre><code>sudo nano /var/ossec/etc/ossec.conf</code></pre>

<p><strong>Set the Manager IP:</strong> Look for the <code>&lt;client&gt;</code> section and replace the <code>&lt;address&gt;</code> field with the IP address of your Wazuh manager. Save your changes and exit the editor.</p>

<p><strong>Enable and Start the Agent Service:</strong> Ensure that the Wazuh agent starts automatically upon system boot:</p>
<pre><code>sudo systemctl daemon-reload
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent</code></pre>
<br />
<br />
Setup Honeypot: <br/>
<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/0*RNhoRpyMWLaojAx-.png" height="80%" width="80%" alt="Disk honeypot Steps"/>
<br />
<br />
Install outdated software:  <br/>
<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*HkzTTGSYVTDrzfBb_1mrrw.png" height="80%" width="80%" alt="Install Outdated Software Steps"/>
<br />
<br />
Analyzing Cyber Attacks:  <br/>
<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*xbcYv97hBblaas1Eyjlxcg.png" height="80%" width="80%" alt="Cyberattack Steps"/>
<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*96MlI7vMd2UlqZ_2WCp_Aw.png" height="80%" width="80%" />
<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*RtG_6mtwvkV063TJtp1AjQ.png" height="80%" width="80%" />
<br />
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
