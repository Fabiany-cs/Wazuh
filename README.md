# Vulnerability Detection with Wazuh
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
  <h1>Description:</h1>
  <p>Welcome to the Vulnerability Detection with Wazuh project! This GitHub repository aims to provide a comprehensive guide and setup for utilizing Wazuh, an open-source security monitoring platform. In addition to vulnerability detection, Wazuh also serves as an XDR (Extended Detection and Response) / EDR (Endpoint Detection and Response) solution, offering threat intelligence, regulatory compliance monitoring, and cloud security capabilities. Whether you're a security enthusiast, a system administrator, or a developer, this project aims to empower you with the tools and knowledge needed to enhance the security of your environments.</p>

  <h1>Features:</h1>
  <ul>
    <li><strong>Wazuh Management Installation:</strong> Step-by-step instructions to install and configure Wazuh management on an Ubuntu virtual machine.</li>
    <li><strong>Agent Deployment:</strong> Learn how to deploy Wazuh agents to multiple virtual machines across your network.</li>
    <li><strong>Vulnerability Monitoring:</strong> Gain insights into potential vulnerabilities and security threats across your network infrastructure.</li>
    <li><strong>Customization:</strong> Tailor Wazuh to fit your specific requirements by exploring advanced configurations and settings.</li>
    <li><strong>Integration:</strong> Explore options for integrating Wazuh with other security tools and platforms to enhance your overall security posture.</li>
  </ul>

<hr>

<h1>Steps:</h1>

<h2>Downloading Ubuntu ISO File for VM</h2>
    <ol>
        <li>Go to <a href="https://ubuntu.com/download/desktop">Ubuntu Download Page</a> and download Ubuntu 22.04.4 LTS ISO image.</li>
        <li>Download the <a href="https://www.virtualbox.org/wiki/Downloads">VirtualBox Platform Package</a> corresponding to your local machine </li>
        <li>Set the Ubuntu VM in Oracle VirtualBox:
            <ul>
                <li>Make sure you allocate a minimum of 4 Gbs of ram and 2 cpus</li>
                <li>Under network settings of the VM, make sure its under "Bridged Network" so all the devices can be on the same subnet.</li>
            </ul>
        </li>
        <li>Launch your Ubuntu VM and wait for the configuration and installation to complete.</li>
    </ol>
    <img width="1437" alt="Screenshot 2024-04-22 at 9 54 20 AM" src="https://github.com/Fabiany-cs/Fabiany-cs/assets/107880960/60986f39-030a-433b-adb6-03c51b4d1fad">
    <img width="1019" alt="Screenshot 2024-04-22 at 9 54 46 AM" src="https://github.com/Fabiany-cs/Fabiany-cs/assets/107880960/953e2860-a229-4192-bd77-22a2dd6f5c09">
    <img width="817" alt="Screenshot 2024-04-22 at 10 00 00 AM" src="https://github.com/Fabiany-cs/Fabiany-cs/assets/107880960/731250c5-9858-47e9-91f3-a5c68113a221">
    <hr>
    <h2>Setting Up Wazuh Manager in Ubuntu Terminal</h2>
    <ol>
        <li>Open up a terminal in the Ubuntu machine and switch to root user.</li>
        <li>Follow the guide on <a href="https://documentation.wazuh.com/current/quickstart.html">Wazuh documentation</a> to install Wazuh on the management server.</li>
        <li>If copy-paste doesn't work, enable bidirectional shared clipboard in VirtualBox settings.</li>
        <li>Run the following command in the terminal:
            <pre><code>curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh && sudo bash ./wazuh-install.sh -a</code></pre>
            <p>If curl is not installed, run: <code>(sudo) apt install curl</code></p>
        </li>
        <li>Copy and paste the provided username and password from the terminal.</li>
        <li>Check your IP address using <code>ifconfig</code>. If not installed, run: <code>(sudo) apt install net-tools</code></li>
        <li>Access Wazuh Manager through Firefox using the IP address obtained. Accept the self-signed certificate and log in with the provided credentials.</li>
    </ol>
    <img width="1437" alt="Screenshot 2024-04-22 at 10 18 12 AM" src="https://github.com/Fabiany-cs/Fabiany-cs/assets/107880960/180d2e06-778d-46d3-9c09-8df608f09076">
    <img width="1061" alt="Screenshot 2024-04-22 at 10 29 23 AM" src="https://github.com/Fabiany-cs/Fabiany-cs/assets/107880960/7488490e-ec96-4b7b-b987-1a83680c5074">
    <img width="1302" alt="Screenshot 2024-04-22 at 10 38 21 AM" src="https://github.com/Fabiany-cs/Fabiany-cs/assets/107880960/9a2d79a6-f857-491a-9386-5addd6ba85a4">
    <img width="1322" alt="Screenshot 2024-04-22 at 4 17 39 PM" src="https://github.com/Fabiany-cs/Fabiany-cs/assets/107880960/907fcf95-715f-4a2a-9acd-f106c32e1375">
    
    <h2>Installing Agents</h2>
    <ol>
        <li>Install 3 agents: 1 on Kali Linux VM and 2 on macOS devices.</li>
        <li>For each agent:
            <ol type="a">
                <li>Choose the appropriate configuration (e.g., Linux (DEB amd64)).</li>
                <li>Use the provided IP address from the server and assign a name.</li>
                <li>Copy and paste the command from the Ubuntu VM to the respective device's command line.</li>
                <li>Start the agent.</li>
            </ol>
        </li>
        <li>Check the status of each agent using <code>systemctl status wazuh-agent</code>.</li>
    </ol>
    <h2>Checking Wazuh Manager</h2>
    <ol>
        <li>In the Ubuntu VM, type <code>systemctl status wazuh-manager</code> to check if it's active and running.</li>
        <li>Verify in the Wazuh dashboard that the agents are activated.</li>
    </ol>
    <h2>Onboard MacMini - Personal Machine</h2>
    <ol>
        <li>Install agent on Mac OS (Intel) using the provided server IP and a name.</li>
        <li>Refresh the Wazuh Dashboard to confirm installation.</li>
        <li>Repeat the process for other personal devices, like MacBookPro.</li>
    </ol>
    <h2>Wazuh Dashboard</h2>
    <p>Explore the Wazuh Dashboard to:</p>
    <ul>
        <li>Investigate security incidents.</li>
        <li>Relate devices with the MITRE Framework.</li>
        <li>View security alerts and descriptions.</li>
        <li>Expand events for further evaluation.</li>
    </ul>
    <h2>Agents Tab</h2>
    <p>In the Agents Tab, you can:</p>
    <ul>
        <li>View activity per agent.</li>
        <li>Check CIS Benchmark compliance.</li>
        <li>See failed benchmarks and remediation steps.</li>
        <li>View compliance based on various standards.</li>
    </ul>
    <h2>Additional XML Configuration</h2>
    <ol>
        <li>Access the Wazuh Manager machine.</li>
        <li>Edit the <code>ossec.conf</code> file located in <code>/var/ossec/etc</code>.</li>
        <li>Enable additional configurations within the XML, such as vulnerability detection.</li>
        <li>Restart the system.</li>
        <li>Check the status using <code>systemctl status wazuh-manager</code>.</li>
    </ol>  
</body>
</html>
