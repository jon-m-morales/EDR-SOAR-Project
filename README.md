<h1> EDR + SOAR Homelab Project </h1>
<h2>Description</h2>
In this project I provide walkthrough documentation starting from the ground up, configuring Lima Charlie EDR and Tines for SOAR capabilities. This lab will be focuses on using these tools to provide orcastration, automation, and response. Tines will provide orcastration acting as our central control plane. Automations will be setup to send alerts via Slack and E-mail. Additionally an autogenertated user prompt will be provided showcasing key alert details and allow us to respond to the threat. The user prompt will ask us to network isolate the endpoint, and based upon our decision we could answer yes, and automate the actions needed to do so.

<h2>Tools used</h2>
  - LimaCharlie<br>
  - Tines<br>
  - Slack<br>
  - E-mail<br>
  - HackTool (Mimikatz)<br>
  - Windows Desktop (Used as compromised host)<br>

<h2>Process Overview</h2>
Create detection in LimaCharlie - Detect Mimikatz > Tines > Slack & Email<br><br>

Tines > Prompt User to isolate the machine (Yes/NO)
- if yes: LimaCharlie should automatically isolate the machine and a message should be sent to Slack.<br>
- if no: LimaCharlie will not isolate.<br>
- Message: Isolation status with note of "The computer <computer> was not isolated, please investigate."<br>

<h2> Playbook Diagram </h2>
<img width="725" height="965" alt="image" src="https://github.com/user-attachments/assets/85bb7468-d829-425f-a20f-39ca9504c56c" />
