<h1> EDR + SOAR Homelab Project </h1>
<h2>Description</h2>
In this project I built a SOAR workflow where LimaCharlie EDR detections are fed to a webhook in Tines. Tines provides orcastration acting as our central control plane. Automations are setup to send alerts via Slack and E-mail. Additionally an autogenertated user prompt will be provided in the alerts showcasing key alert details, allowing us to respond to the threat. The user prompt will ask us if we want to network isolate the endpoint, and based upon our analysis we could answer yes, and automate the actions needed to do so.

<h2>Tools Used</h2> 

- LimaCharlie 
- Tines 
- Slack 
- E-mail 
- HackTool (Mimikatz)

<h2>Enviornments Used</h2>

- Windows 11 (Used as compromised host)

<h2>Process Overview</h2>
Create detection in LimaCharlie - Detect Mimikatz > Tines > Slack & Email<br><br>

Tines > Prompt User to isolate the machine (Yes/NO)
- if yes: LimaCharlie should automatically isolate the machine and a message should be sent to Slack.<br>
- if no: LimaCharlie will not isolate.<br>
- Message: Isolation status with note of "The computer <computer> was not isolated, please investigate."<br>

<h2> Playbook Diagram </h2>
<img width="725" height="965" alt="image" src="https://github.com/user-attachments/assets/85bb7468-d829-425f-a20f-39ca9504c56c" />

<h2>Tines Story</h2>
<img width="869" height="1147" alt="image" src="https://github.com/user-attachments/assets/717bb60d-fd9d-443d-b9cb-49050f6494fd" />

<h2>SOAR WorkFlow Walkthrough</h2>
1) Mimikatz is ran, EDR detects and sends to Tines to generate alerts & user promt.
<img width="1494" height="749" alt="Mimikatz ran on compromised host" src="https://github.com/user-attachments/assets/0c777af2-97c2-4dfa-8db8-09a4d14b2bc6" />
<img width="973" height="720" alt="Initial Slack Alert" src="https://github.com/user-attachments/assets/d2f55ec2-eb83-47f0-aa31-b5485e9b70fb" />
<img width="1143" height="514" alt="Initial E-mail Alert" src="https://github.com/user-attachments/assets/776beef2-60b7-45ab-9dec-157531a2963f" />
<img width="726" height="833" alt="User Prompt for host Network Isolation" src="https://github.com/user-attachments/assets/f4954c3d-afa0-49ee-9f51-3b1479d3da5d" /><br><br>
2) After carfully analyzing detection, we decice to isolate host from network. So we click yes and submit on the user prompt.
<img width="726" height="833" alt="Submit resolution screen" src="https://github.com/user-attachments/assets/bce6bc40-2adf-4352-a96e-002e296807eb" /><br><br>
3)Slack sends a message with computer name and verified sensor isolation status.
<img width="983" height="716" alt="Slack Isolation Status Message" src="https://github.com/user-attachments/assets/81bea0c1-5685-41d9-9b65-51ce0a84081a" /><br><br>
4) Lets navigate to EDR to verify the automation has worked as intended.
<img width="934" height="762" alt="image" src="https://github.com/user-attachments/assets/a3d77865-8fbf-4c93-b72f-587837c39613" />

