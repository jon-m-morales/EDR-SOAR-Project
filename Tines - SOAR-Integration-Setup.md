<h1>SOAR Integration</h1>
<h3>In this section I will be going over how to link Tines to LimaCharlie, Slack, and E-mail for detection automations.</h3>
<h2>Tines Webhook configuration</h2>
Create a Tines account at https://www.tines.com, open a story and ensure its clear of actions. Now drag over the Webhook action onto the story board and fill out as shown in image below.<br>
<img width="1245" height="894" alt="image" src="https://github.com/user-attachments/assets/e82ca3c7-6686-47de-a32d-fcf882138055" /><br><br>
Now copy the Webhook URL and move over to LimaCharlie, and navigate to Output > add output. Select the detections output and then select Tines.
Configure it by creating a name, and set destination host as the webhook url we copied. Once completed hit Save Output. We may need to re-launch mimikatz on endpoint to generate sample, once we can view a sample we know it's worked.
<img width="1354" height="297" alt="image" src="https://github.com/user-attachments/assets/d5f2e596-93f0-46e9-8c9d-7c108816be4b" />
<img width="661" height="361" alt="image" src="https://github.com/user-attachments/assets/ee77921e-e9e2-426d-bc85-96946892a64f" /><br>
Move back to Tines, and click the webhook action, and events. We should see an event.
<img width="1937" height="1160" alt="image" src="https://github.com/user-attachments/assets/2b36eaf6-db6a-4472-9fe5-0f3788db22a2" /><br><br>

<h2>Slack Integration Setup</h2>
Create slack account at https://www.slack.com and create a new channel called alerts.<br>
<img width="1530" height="833" alt="image" src="https://github.com/user-attachments/assets/973cec93-d3e4-4f92-b5fc-958f8a2fcaeb" /><br>
Now in Slack, navigate to More > Apps > Search "Tines" > Click install button<br>
On the next screen select the Add To Slack button<br>
<img width="1232" height="652" alt="image" src="https://github.com/user-attachments/assets/774e69c8-6726-4743-8d69-e3a774643d72" /><br>
Lets complete the integration and Move back to Tines. Now navigate to Team Menu > Credentials and press the + button to add a new credential.<br>
<img width="1955" height="872" alt="image" src="https://github.com/user-attachments/assets/96d195fd-43a6-4965-b46e-3d377b021239" />
Next we'll highlight Slack, and press create credential. On the next screen I will be selecting Tines app for Slack. And finally allow Tines app to access Slack.<br>
<img width="789" height="713" alt="image" src="https://github.com/user-attachments/assets/8d1371ef-e24c-463e-a7e0-9e6874bcf66c" />
<img width="587" height="644" alt="image" src="https://github.com/user-attachments/assets/80d00e45-3634-40de-af3e-607d72be0020" />
<img width="1140" height="325" alt="image" src="https://github.com/user-attachments/assets/21e652d5-9b06-41da-a16e-81567d20eda8" /><br>
Back on our Tines story, lets navigate to Templates > Slack > Search "Send a message"  and drag it over into the story.
<img width="1109" height="726" alt="image" src="https://github.com/user-attachments/assets/8753fd92-fd43-4627-a772-3ac3aa60f010" >
Now lets quickly move back to slack, right click the alerts channel, and select "view channel details". Now copy the channel id in the lower section of the pop-up and move back to Tines.<br>
Paste the ID into the Slack action field for the channel id. Connect the webhook to our slack action and run the slack action to test. If you see a message in the Slack alerts channel, you have sucessfully made the connection.
<img width="970" height="749" alt="image" src="https://github.com/user-attachments/assets/8a771cd1-af6d-445a-9188-c4f7593f21d7" />

<h2>E-mail Setup</h2>
Drag over the e-mail action onto the story and connect the Webhook to it. On the Build tab on the right panel, fill out the Recipients, Reply to, and Subject fields. I left the e-mail addresses defaulted to my account address, and updated the subject to "Security Alerts"
Next we can test by pressing the test button, and selecting one of our detections, and hitting the test button. We should see the e-mail in our inbox.<br>
<img width="906" height="423" alt="image" src="https://github.com/user-attachments/assets/c914e38a-2ee3-4d6f-bfb0-4c2ec7810ef4" />
<img width="707" height="505" alt="image" src="https://github.com/user-attachments/assets/d285a264-2ca9-4431-b510-c7a22513a7c6" />

<h2>User Prompt Setup</h2>
As depicted in our diagram, not only will Tines send us alerts via slack & e-mail, but it will also get a user promot for decision making.
On the Story, select tools in the left pane, and drag on the page action.<br>
Fill it out with the following details - <br>
* Name: User Prompt<br>
* Description: Isolate Computer (Yes/No)<br> 
* Success Message: Thank you, you can now close this window.<br>
Now lets edit the page by double clicking create page, or edit page button. Then add a header, rich text, and boolean. Modify it with the information detailed in the image below.<br>
<img width="476" height="327" alt="image" src="https://github.com/user-attachments/assets/d4776bf7-40f8-4ba6-9741-3fc43e80faf1" /><br>

<h2>Inserting Alert Data</h2>
Go to the Webhook events, and copy & paste the path for the following fields onto a text file - <br>
Under body copy Cat and link.<br>
Under body>detect>event copy COMMAND_LINE, File_Path, and User_name <br>
Under body>detect>routing copy hostname, int_ip, and sid.<br>
Organize then as you see fit, add names for each field, and paste them into the Slack action message field.<br>
<img width="1937" height="1055" alt="image" src="https://github.com/user-attachments/assets/d7e1c517-b076-484d-a6d9-a204dd9d0c02" />
<img width="319" height="641" alt="image" src="https://github.com/user-attachments/assets/7c94e73d-fa46-4672-9323-31b26caed0b9" /><br>
Now we will do this for e-mails. Goto the E-mail action and paste the same data from slack into the body field. Now open the HTML editor.<br>
We will need to add "<br>" on each field to create new lines, and optionally "<b></b>" on the names to make the formating more legible. Make sure to send a test once completed to ensure it's working.<br>
<img width="1492" height="270" alt="image" src="https://github.com/user-attachments/assets/7b38452a-7923-4d99-b9c0-56722e827859" /><br>
Now we will do this again for our User Prompt. Edit the page, and paste the Slack Message we crafted earilier into the rich text field.<br>
<img width="742" height="492" alt="image" src="https://github.com/user-attachments/assets/7dd38e03-eebc-41f8-9788-61da6c4e0b07" />

<h2>Isolate Function Setup</h2>
Drag the Trigger Action on to the story.

