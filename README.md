<h1> EDR + SOAR Homelab Project </h1>
<h3>This page contains a high level objectives for EDR + SOAR Homelab project </h3>
Story - Tines
Create detection in LimaCharlie - Detect HackTool > Tines > Discord & Email

Slack & Email will contain
- Time
- Computer Name
- Source IP
- Process
- Command Line
- File Path
- Sensor ID
- Link to detection (if applicable)

Tines > Prompt User to isolate the machine (Yes/NO)
- if yes: LimaCharlie should automatically isolate the machine and a message should be sent to Slack
- if no: LimaCharlie will not isolate
- Message: Isolation status with note of "The computer <computer> was not isolated, please investigate."

<h1> Playbook Diagram </h1>
<img width="725" height="965" alt="image" src="https://github.com/user-attachments/assets/85bb7468-d829-425f-a20f-39ca9504c56c" />
