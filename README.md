<h1> EDR + SOAR Homelab Project </h1>
<h2>Description</h2>
In this project I built a SOAR workflow where LimaCharlie EDR detections are feed to a webhook in Tines. Tines provides orcastration acting as our central control plane. Automations are setup to send alerts via Slack and E-mail. Additionally an autogenertated user prompt will be provided in the alerts showcasing key alert details, allowing us to respond to the threat. The user prompt will ask us if we want to network isolate the endpoint, and based upon our analysis we could answer yes, and automate the actions needed to do so.

<h2>Tools Used</h2> 

- LimaCharlie 
- Tines 
- Slack 
- E-mail 
- HackTool (Mimikatz)

<h2>Enviornments Used</h2>

- Windows 11 Desktop (Used as compromised host)

<h2>Process Overview</h2>
Create detection in LimaCharlie - Detect Mimikatz > Tines > Slack & Email<br><br>

Tines > Prompt User to isolate the machine (Yes/NO)
- if yes: LimaCharlie should automatically isolate the machine and a message should be sent to Slack.<br>
- if no: LimaCharlie will not isolate.<br>
- Message: Isolation status with note of "The computer <computer> was not isolated, please investigate."<br>

<h2> Playbook Diagram </h2>
<img width="725" height="965" alt="image" src="https://github.com/user-attachments/assets/85bb7468-d829-425f-a20f-39ca9504c56c" />
