<h1>SOAR Integration</h1>
Create slack account at https://www.slack.com and create a new channel called alerts.<br>
<img width="1530" height="833" alt="image" src="https://github.com/user-attachments/assets/973cec93-d3e4-4f92-b5fc-958f8a2fcaeb" /><br><br>
Create a Tines account at https://www.tines.com, open a story and ensure its clear of actions. Now drag over the Webhook action onto the sotry board and fill out as shown in image below.<br>
<img width="1245" height="894" alt="image" src="https://github.com/user-attachments/assets/e82ca3c7-6686-47de-a32d-fcf882138055" /><br><br>
Now copy the Webhook URL and move over to LimaCharlie, and navigate to Output > add output. Select the detections output and then select tines.
Configure it by creating a name, and set destination host as the webhook url we copied. Once completed hit Save Output. We may need to re-launch mimikatz on endpoint to generate sample, once we can view a sample we know it's worked.
<img width="1354" height="297" alt="image" src="https://github.com/user-attachments/assets/d5f2e596-93f0-46e9-8c9d-7c108816be4b" /><br>


Move back to tines, and click the webhook action, and events. We should see an event.
<img width="1937" height="1160" alt="image" src="https://github.com/user-attachments/assets/2b36eaf6-db6a-4472-9fe5-0f3788db22a2" />

