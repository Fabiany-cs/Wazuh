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
        <li>Set up a VM in Oracle VirtualBox with the following credentials:
            <ul>
                <li>Username: wazuhadmin</li>
                <li>Password: wazuhpassword123!</li>
            </ul>
        </li>
        <li>Launch your Ubuntu VM and wait for the configuration and installation to complete.</li>
    </ol>
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
