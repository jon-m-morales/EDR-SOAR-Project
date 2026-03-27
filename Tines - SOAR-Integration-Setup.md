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

<h2>Slack - Part 1 - Integration Setup</h2>
Create slack account at https://www.slack.com and create a new channel called alerts.<br>
<img width="1530" height="833" alt="image" src="https://github.com/user-attachments/assets/973cec93-d3e4-4f92-b5fc-958f8a2fcaeb" /><br>
Now in Slack, navigate to More > Apps > Search "Tines" > Click install button<br>
On the next screen select the Add To Slack button<br>
<img width="1232" height="652" alt="image" src="https://github.com/user-attachments/assets/774e69c8-6726-4743-8d69-e3a774643d72" /><br>
Lets complete the integration and Move back to Tines. Now navigate to Team Menu > Credentials and press the + button to add a new credential.<br>
<img width="1955" height="872" alt="image" src="https://github.com/user-attachments/assets/96d195fd-43a6-4965-b46e-3d377b021239" />
Next we'll highlight Slack, and press create credential. On the next screen I will be selecting Tines app for Slack. And finally allow Tines app to access Slack.
<img width="789" height="713" alt="image" src="https://github.com/user-attachments/assets/8d1371ef-e24c-463e-a7e0-9e6874bcf66c" />
<img width="587" height="644" alt="image" src="https://github.com/user-attachments/assets/80d00e45-3634-40de-af3e-607d72be0020" />
<img width="1140" height="325" alt="image" src="https://github.com/user-attachments/assets/21e652d5-9b06-41da-a16e-81567d20eda8" />

<h2>Slack - Part 2 - Alert Setup</h2>
Back on our Tines story, lets navigate to Templates > Slack > Search "Send a message"  and drag it over into the story.
<img width="1109" height="726" alt="image" src="https://github.com/user-attachments/assets/8753fd92-fd43-4627-a772-3ac3aa60f010" >
Now lets quickly move back to slack, right click the alerts channel, and select "view channel details". Now copy the channel id in the lower section of the pop-up and move back to Tines.<br>
Paste the ID into the Slack action field for the channel id. Connect the webhook to our slack action and run the slack action to test. If you see a message in the Slack alerts channel, you have sucessfully made the connection.
<img width="970" height="749" alt="image" src="https://github.com/user-attachments/assets/8a771cd1-af6d-445a-9188-c4f7593f21d7" />

