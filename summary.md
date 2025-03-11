# Summary of the SOC Automation Lab Project
The SOC Automation Lab project is a comprehensive initiative aimed at creating an automated Security Operations Center (SOC) workflow to enhance the efficiency and effectiveness of security monitoring, alerting, and incident response. By leveraging open-source tools like Wazuh, Shuffle, and TheHive, this project automates key SOC processes, reducing manual intervention and improving response times to security incidents. Below is a detailed summary of the project, broken down into its key components and steps, to provide a clear understanding of how the project was executed.

## 1. Project Overview
The primary goal of the SOC Automation Lab is to automate the collection, analysis, and response to security events in real-time. The project focuses on:

Automating Event Collection and Analysis: Using tools like Sysmon and Wazuh to collect and analyze security events from a Windows 10 client machine.

Streamlining Alerting Processes: Automating the generation and forwarding of alerts to relevant systems and personnel.

Enhancing Incident Response: Automating response actions to security incidents using Shuffle and TheHive.

Improving SOC Efficiency: Reducing the workload on SOC analysts by automating routine tasks, allowing them to focus on high-priority issues.

The project involves setting up a Windows 10 client machine with Sysmon for detailed event logging, a Wazuh server for event management and alerting, TheHive for case management, and Shuffle for workflow automation. The integration of these tools creates a seamless, automated SOC workflow.

## 2. Prerequisites
Before starting the project, the following prerequisites were addressed:

### 2.1 Hardware Requirements
A host machine capable of running multiple virtual machines (VMs) simultaneously.

Sufficient CPU, RAM, and disk space to support the VMs and their workloads.

### 2.2 Software Requirements
VMware Workstation/Fusion: Used for creating and managing VMs.

Windows 10: The client machine for generating security events.

Ubuntu 22.04: The operating system for deploying Wazuh and TheHive.

Sysmon: A Windows system monitoring tool for detailed event logging.

### 2.3 Tools and Platforms
Wazuh: An open-source security monitoring platform for event collection, analysis, and alerting.

Shuffle: A security automation platform for workflow automation.

TheHive: A security incident response platform for case management.

VirusTotal: A service for analyzing files and URLs for malicious content.

### 2.4 Prior Knowledge
Basic understanding of virtual machines, Linux command-line operations, and security monitoring concepts.

## 3. Setup
The setup phase involved configuring the Windows 10 client, Wazuh server, TheHive, and Shuffle.

### 3.1 Windows 10 Client with Sysmon
Step 1: Installed Windows 10 on VMware.

Step 2: Downloaded and installed Sysmon for detailed event logging.

Step 3: Configured Sysmon using a modular configuration file to monitor specific events.

Step 4: Verified Sysmon installation by checking the Windows Event Viewer.

### 3.2 Wazuh Server Setup
Step 1: Created a DigitalOcean Droplet with Ubuntu 22.04 for the Wazuh server.

Step 2: Configured a firewall to restrict access to the Wazuh server.

Step 3: Installed Wazuh using the official installation script.

Step 4: Accessed the Wazuh web interface and logged in using the generated credentials.

### 3.3 TheHive Setup
Step 1: Created another DigitalOcean Droplet for TheHive.

Step 2: Installed dependencies like Java, Cassandra (database), and Elasticsearch (search engine).

Step 3: Installed TheHive and configured it to work with Cassandra and Elasticsearch.

Step 4: Accessed TheHive via the web interface using default credentials.

### 3.4 Wazuh and TheHive Integration
Step 1: Added a Windows agent to Wazuh for event collection from the Windows 10 client.

Step 2: Configured Wazuh to forward Sysmon events to the Wazuh server.

Step 3: Verified that events from the Windows client were being received in Wazuh.

## 4. Generating Telemetry and Custom Alerts
This phase focused on generating security events and creating custom alerts in Wazuh.

### 4.1 Sysmon Event Forwarding
Modified the Wazuh agent configuration to forward Sysmon events to the Wazuh server.

Verified that Sysmon events were being received in the Wazuh web interface.

### 4.2 Mimikatz Telemetry
Downloaded and executed Mimikatz on the Windows client to simulate an attacker extracting credentials.

Configured Wazuh to log all events, including those that do not trigger alerts.

Verified that Mimikatz events were being logged in Wazuh.

### 4.3 Custom Mimikatz Alert
Created a custom rule in Wazuh to detect Mimikatz usage based on the originalfilename field.

Tested the custom rule by renaming the Mimikatz executable and verifying that the alert was triggered.

## 5. Automation with Shuffle and TheHive
This phase involved integrating Shuffle and TheHive to automate incident response workflows.

### 5.1 Shuffle Setup
Created a Shuffle account and set up a new workflow.

Added a Webhook trigger to receive alerts from Wazuh.

Configured Wazuh to send alerts to Shuffle using the webhook URL.

### 5.2 Mimikatz Workflow
Step 1: Extracted the SHA256 hash of the Mimikatz executable using a regex in Shuffle.

Step 2: Integrated VirusTotal to check the reputation of the extracted hash.

Step 3: Integrated TheHive to create an alert for the Mimikatz detection.

Step 4: Configured Shuffle to send an email notification to the SOC analyst with details of the alert.

## 6. Conclusion
The SOC Automation Lab project successfully demonstrated how to automate key SOC processes using open-source tools. The project achieved the following:

Automated event collection and analysis using Sysmon and Wazuh.

Streamlined alerting and incident response using Shuffle and TheHive.

Created custom alerts for specific threats like Mimikatz.

Built an automated workflow to extract file hashes, check reputations, create alerts, and notify analysts.

This project provides a solid foundation for further customization and expansion of SOC automation workflows. By continuously refining these workflows and integrating additional tools, organizations can enhance their security operations, improve incident response times, and reduce the workload on SOC analysts.

### Key Takeaways
Automation is Key: Automating routine tasks like event collection, alerting, and incident response significantly improves SOC efficiency.

Open-Source Tools are Powerful: Tools like Wazuh, TheHive, and Shuffle provide robust capabilities for building an automated SOC.

Customization is Essential: Custom rules and workflows allow organizations to tailor their SOC automation to specific threats and requirements.

Continuous Improvement: Regularly updating and refining automation workflows ensures that the SOC remains effective against evolving threats.

This project serves as a practical guide for implementing SOC automation and can be adapted to meet the unique needs of any organization.

give me a more detailed summary so that whenever i read it , gives me a complete understanding and revision of this project
Detailed Summary of the SOC Automation Lab Project
The SOC Automation Lab project is an in-depth initiative designed to create an automated Security Operations Center (SOC) workflow. The goal is to streamline the processes of event monitoring, alerting, and incident response by leveraging powerful open-source tools like Wazuh, Shuffle, and TheHive. This project not only enhances the efficiency of SOC operations but also reduces manual intervention, allowing SOC analysts to focus on high-priority tasks. Below is a comprehensive and detailed summary of the project, broken down into its key phases, to provide a complete understanding and serve as a revision guide.

### 1. Project Overview
The SOC Automation Lab project aims to automate the following key SOC processes:

Event Collection and Analysis: Automatically collect and analyze security events in real-time using tools like Sysmon and Wazuh.

Alerting: Automate the generation and forwarding of alerts to relevant systems and personnel.

Incident Response: Automate response actions to security incidents using Shuffle and TheHive.

SOC Efficiency: Reduce the workload on SOC analysts by automating routine tasks, enabling them to focus on strategic initiatives.

The project involves setting up a Windows 10 client machine with Sysmon for detailed event logging, a Wazuh server for event management and alerting, TheHive for case management, and Shuffle for workflow automation. The integration of these tools creates a seamless, automated SOC workflow.

### 2. Prerequisites
Before starting the project, the following prerequisites were addressed:

#### 2.1 Hardware Requirements
A host machine capable of running multiple virtual machines (VMs) simultaneously.

Sufficient CPU, RAM, and disk space to support the VMs and their workloads.

#### 2.2 Software Requirements
VMware Workstation/Fusion: Used for creating and managing VMs.

Windows 10: The client machine for generating security events.

Ubuntu 22.04: The operating system for deploying Wazuh and TheHive.

Sysmon: A Windows system monitoring tool for detailed event logging.

#### 2.3 Tools and Platforms
Wazuh: An open-source security monitoring platform for event collection, analysis, and alerting.

Shuffle: A security automation platform for workflow automation.

TheHive: A security incident response platform for case management.

VirusTotal: A service for analyzing files and URLs for malicious content.

#### 2.4 Prior Knowledge
Basic understanding of virtual machines, Linux command-line operations, and security monitoring concepts.

### 3. Setup
The setup phase involved configuring the Windows 10 client, Wazuh server, TheHive, and Shuffle.

#### 3.1 Windows 10 Client with Sysmon
Step 1: Installed Windows 10 on VMware.

Step 2: Downloaded and installed Sysmon for detailed event logging.

Step 3: Configured Sysmon using a modular configuration file to monitor specific events.

Step 4: Verified Sysmon installation by checking the Windows Event Viewer.

#### 3.2 Wazuh Server Setup
Step 1: Created a DigitalOcean Droplet with Ubuntu 22.04 for the Wazuh server.

Step 2: Configured a firewall to restrict access to the Wazuh server.

Step 3: Installed Wazuh using the official installation script.

Step 4: Accessed the Wazuh web interface and logged in using the generated credentials.

#### 3.3 TheHive Setup
Step 1: Created another DigitalOcean Droplet for TheHive.

Step 2: Installed dependencies like Java, Cassandra (database), and Elasticsearch (search engine).

Step 3: Installed TheHive and configured it to work with Cassandra and Elasticsearch.

Step 4: Accessed TheHive via the web interface using default credentials.

#### 3.4 Wazuh and TheHive Integration
Step 1: Added a Windows agent to Wazuh for event collection from the Windows 10 client.

Step 2: Configured Wazuh to forward Sysmon events to the Wazuh server.

Step 3: Verified that events from the Windows client were being received in Wazuh.

### 4. Generating Telemetry and Custom Alerts
This phase focused on generating security events and creating custom alerts in Wazuh.

#### 4.1 Sysmon Event Forwarding
Modified the Wazuh agent configuration to forward Sysmon events to the Wazuh server.

Verified that Sysmon events were being received in the Wazuh web interface.

4.2 Mimikatz Telemetry
Downloaded and executed Mimikatz on the Windows client to simulate an attacker extracting credentials.

Configured Wazuh to log all events, including those that do not trigger alerts.

Verified that Mimikatz events were being logged in Wazuh.

#### 4.3 Custom Mimikatz Alert
Created a custom rule in Wazuh to detect Mimikatz usage based on the originalfilename field.

Tested the custom rule by renaming the Mimikatz executable and verifying that the alert was triggered.

### 5. Automation with Shuffle and TheHive
This phase involved integrating Shuffle and TheHive to automate incident response workflows.

#### 5.1 Shuffle Setup
Created a Shuffle account and set up a new workflow.

Added a Webhook trigger to receive alerts from Wazuh.

Configured Wazuh to send alerts to Shuffle using the webhook URL.

#### 5.2 Mimikatz Workflow
Step 1: Extracted the SHA256 hash of the Mimikatz executable using a regex in Shuffle.

Step 2: Integrated VirusTotal to check the reputation of the extracted hash.

Step 3: Integrated TheHive to create an alert for the Mimikatz detection.

Step 4: Configured Shuffle to send an email notification to the SOC analyst with details of the alert.

### 6. Conclusion
The SOC Automation Lab project successfully demonstrated how to automate key SOC processes using open-source tools. The project achieved the following:

Automated event collection and analysis using Sysmon and Wazuh.

Streamlined alerting and incident response using Shuffle and TheHive.

Created custom alerts for specific threats like Mimikatz.

Built an automated workflow to extract file hashes, check reputations, create alerts, and notify analysts.

This project provides a solid foundation for further customization and expansion of SOC automation workflows. By continuously refining these workflows and integrating additional tools, organizations can enhance their security operations, improve incident response times, and reduce the workload on SOC analysts.

Key Takeaways
Automation is Key: Automating routine tasks like event collection, alerting, and incident response significantly improves SOC efficiency.

Open-Source Tools are Powerful: Tools like Wazuh, TheHive, and Shuffle provide robust capabilities for building an automated SOC.

Customization is Essential: Custom rules and workflows allow organizations to tailor their SOC automation to specific threats and requirements.

Continuous Improvement: Regularly updating and refining automation workflows ensures that the SOC remains effective against evolving threats.

This project serves as a practical guide for implementing SOC automation and can be adapted to meet the unique needs of any organization.
