# Wazuh-SIEM-_-to_SOAR_implementation

### Preview
___

This project is aimed to create familiarization and use of SIEM not just to collect data but also to automate and orchestrate incident response. This process helps to respond to security incident faster. 

### Skills (*learned*)
___
Bullet Point

- SIEM
- System Auditing
- Installation of Wazuh server and agent deployment
- Integration of intrusion detection system (suricata) on Wazuh (SIEM)
- Installation of IDS (suricata)
- Log analysis

### Tools 
___

Wazuh - Security incident and event management tool [Download Here](Https://www.Wazuh.com)

Suricata - Intrusion detection system

Kali Linux - Debian Based OS [Download Here](Https://www.kali.org)

Oracle virtual box - [Download Here](Https://www.virtualbox.com)

### Procedures
___

1. Download the wazuh server from the wazuh official page
2. I installed the server by importing it on the virtual box as this required minimum of 2gb ram and 2 cpu. Set the graphics controller on my virtual box to *VMSVGA* as Wazuh only works with *VMSVGA* on virtual box. Start the wazuh server machine



<img width="1280" alt="Screenshot 2024-06-05 at 18 14 41" src="https://github.com/USENEDEM/Wazuh-SIEM-_-to_SOAR_implementation/assets/169564406/3416e160-186d-4313-93d8-82b5d924b9a0">



<img width="1280" alt="Screenshot 2024-06-05 at 18 19 31" src="https://github.com/USENEDEM/Wazuh-SIEM-_-to_SOAR_implementation/assets/169564406/eb0498e9-a53c-491d-bf4a-3c4611e74ce6">

*Ref 1* (import appliance) *Ref 2* (VMSVGA selection)

3. Logged into the wazuh server,checked for the wazuh ip address and log into the wazuh manager using my browser and ip credentials of wazuh.



<img width="1280" alt="Screenshot 2024-06-05 at 18 44 38" src="https://github.com/USENEDEM/Wazuh-SIEM-_-to_SOAR_implementation/assets/169564406/3dfa4d24-8f71-494f-be6f-37f862c11656">


<img width="1280" alt="Screenshot 2024-06-05 at 19 11 16" src="https://github.com/USENEDEM/Wazuh-SIEM-_-to_SOAR_implementation/assets/169564406/ebd6217b-99f3-4592-9286-eca009862521">

*Ref 3* (wazuh server) *Ref 4* (wazuh manager log in )


4. Clicked on the deploy new agent and deployed my kali linux machine on the wazuh manager (Assign a name and server address). Started up the wazuh agent via my linux terminal using the command

   ```zsh
   sudo systemctl start wazuh -agent
   ```



<img width="1280" alt="Screenshot 2024-06-06 at 13 29 13" src="https://github.com/USENEDEM/Wazuh-SIEM-_-to_SOAR_implementation/assets/169564406/0a69a115-9778-4a36-8701-9eccd61cb8db">



<img width="1280" alt="Screenshot 2024-06-06 at 23 32 00" src="https://github.com/USENEDEM/Wazuh-SIEM-_-to_SOAR_implementation/assets/169564406/487b59b5-0f2a-47ce-b41b-29fc12e0de22">

*Ref 5* (adding wazuh agent) *Ref 6* (successfully deployed agent)


5. Installed suricata on my kali linux, edited and added a local file log format (json.file) into the ossec.conf file to allow the agent to send back the var/log/suricata/eve.json file to the wazuh manager. Removed the snort log file to debug errors from the agent while trying to forward the suricata log.
  
6. I copied and added the suricata log file in if.json format to the wazuh manager dashboard file log. i started up the suricata with the command

   ```zsh
   sudo systemctl start suricata.service
   ```

   Suricata logs were now forwarded to wazuh (soar implementation). Used the wazuh for system audit and analysing log files.
   


<img width="1280" alt="Screenshot 2024-06-06 at 23 59 11" src="https://github.com/USENEDEM/Wazuh-SIEM-_-to_SOAR_implementation/assets/169564406/3eacfe37-6d93-4743-8a5a-9ceb3ef20b14">



<img width="1280" alt="Screenshot 2024-06-08 at 12 00 14" src="https://github.com/USENEDEM/Wazuh-SIEM-_-to_SOAR_implementation/assets/169564406/7b8a9763-9c3f-4fb7-8d2e-131af96b63a8">



*Ref 6 & 7* ( system configuration assessment/audit)



<img width="1280" alt="Screenshot 2024-06-08 at 01 14 51" src="https://github.com/USENEDEM/Wazuh-SIEM-_-to_SOAR_implementation/assets/169564406/f8f11284-1336-4870-9d81-42d7078ac399">

*Ref 7* (logs)


