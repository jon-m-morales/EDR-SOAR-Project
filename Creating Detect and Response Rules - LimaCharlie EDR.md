<h1>Detection and Response Rule Creation</h1>
<h3>In this guide I will be explaining how to create your own detection rules</h3>
<h2>Setup Files</h2>
<b> 
You will need to download your malware onto the endpoint which has LimaCharlie installed. <br>
In my example I will be using mimikatz which can be downloaded at https://github.com/ParrotSec/mimikatz/tree/master. <br><br>
<i>
Note:<br>
You may need to disable real time protection on Windows OS, or else it may block or quarantine the malware.
</i>
Additionally, we will create our rules by using a pre-existing rule set, and modifying it for our needs.<br><br>

The rule linked below has been chosen as our template because it's similar to mimicatz in that they detect software meant to harvest credentials.<br>
https://raw.githubusercontent.com/refractionPOINT/sigma-limacharlie/refs/heads/rules/latest/windows_process_creation/proc_creation_win_device_credential_deployment.yml <br>
<img width="652" height="470" alt="image" src="https://github.com/user-attachments/assets/723b51d8-a025-41cb-9398-3e4ec8e28cea" />

<h2>Running the Malware</h2>
Screenshot below depicts mimikatz running on my endpoint, and in the next section I will show the log generated for running this process.<br>
<img width="743" height="248" alt="image" src="https://github.com/user-attachments/assets/3a03bb0d-a8a2-455e-badf-f9c47850d37e" />

<h2>Creating Detection and Response Rules</h2>
In this section I will go through the pre-existing rule set and explain what changes are being made and why.
Below you will find a screenshot of the logged mimikatz proccess ran on the endpoint, which can be found at "Sensors > Sensors List > ENDPOINT_HOSTNAME > Timeline" and search for mimikatz or the name of your process/malware.<br>
<img width="2206" height="747" alt="image" src="https://github.com/user-attachments/assets/e2fa8284-ef45-4d2f-bddd-0f3e9b4f017a" /><br><br>
In the image above I highlighted the items we will be focusing on for detection, which includes matching NEW_PROCESS, FILE_PATH, and/or HASH.<br><br>
To start creating our detection navigate to Detection > D&R Rules > Add Rule. Then copy and paste the detect and response code into their respective section in Lima Charlie.<br><br>

1. The first portion we will leave events as is, matching on New_process and Existing_process. This is because we want to base our search on New process, which is what I have highlighted in my image, and any currently running processes that match mimikatz.
2. op is operator, currently set to "and". This will also stay, so we can add rules.
3. Under first set of rules we have "op: is windows", this will also stay the same since we're detecting mimikatz.exe.
4. Now the first this we will change is adding the or operator to match on File path, or file hash. So we will add a new line and "- op: or" and a new line for "rules:"
5. The next three lines will remain the same but we will modify the value field to be our malware "mimikatz.exe". 
6. Next, we're going to copy our last three lines and modify them to match the file hash.<br>
	The case sensitive field remains at false, op will change to is, and path will be set to event/HASH. Then add the hash into the value field.
7. Our code we should similar to the image below:<br>
	<img width="598" height="487" alt="image" src="https://github.com/user-attachments/assets/1b543a75-b14a-4926-a151-805bf739cf5d" /><br>

Now we will begin modifying the Response code.<br><br>
We can remove the references section and the tag attack.t1218 as they are unnecessary for our purposes. Then update author to our name, update description to match mimikatz detection, level should be upgraded to high, the tag should be attack.credential_access, and we can update the name as we see fit.<br>
The Response code should look similar to this:<br>
<img width="572" height="294" alt="image" src="https://github.com/user-attachments/assets/44f08890-c002-41a3-9a6c-8552f5d7347b" />

<h2>Testing the Rules</h2>
If we go back to our event from the timeline we can press the copy event button.<br>
<img width="858" height="477" alt="image" src="https://github.com/user-attachments/assets/f51b1f6d-18e4-49d9-b0c9-769306571c79" /><br>
Then back on our rules page, scroll down and press "Target Event", then paste our copied event log. Now press Test Event button.
My image below shows 4/4 operations were evaluated and matched successfully<br>
<img width="719" height="1130" alt="image" src="https://github.com/user-attachments/assets/e0fd74a5-b4a8-4e2e-a972-8cfdb5dc2976" />

</b>
