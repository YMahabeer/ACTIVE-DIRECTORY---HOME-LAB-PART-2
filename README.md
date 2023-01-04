# Common Active Directory Tasks to Learn  
Let’s do a few common tasks that are performed using Active Directory.  
1.	Finding users  
You will need to find a user in Active Directory before you can make any changes to their account. You can search manually for a user by going through the Organizational Units and finding where their account is located. A better way is to use the “Find” feature which allows you to search using keywords.
<br><br/>
To use the Find feature; right click on the domain or any Organizational Unit. Then select Find.  
![image](https://user-images.githubusercontent.com/121589466/210334101-967f3aec-e86a-4843-ab4d-83b87b113898.png)  
You can now enter the name of the user and it will return user accounts that contain those search terms you entered. Double click on the desired user to open their account.  
![image](https://user-images.githubusercontent.com/121589466/210334209-9facc313-0fac-4f46-a624-e3cae21b0eec.png)  
You can modify what you search for using the “find” dropdown menu. The “In” drop down menu can also be used to select what location and O.U you want to search in.  
![image](https://user-images.githubusercontent.com/121589466/210334224-66a66d63-9336-4327-bc12-30e81225197a.png)  

2.	Unlock accounts  
If a user tries too many times to logon to their account unsuccessfully, they will be locked out. To unlock a user’s account; double click on their name to open their user properties. Go to the account tab. Check the Unlock account box. Then hit apply.  
![image](https://user-images.githubusercontent.com/121589466/210334248-4e3a55ea-a6c9-41e6-a066-6bd2635ede60.png)  

3.	Reset passwords  
To reset the password on a user’s account; right click on their name and click on Reset Password.  
![image](https://user-images.githubusercontent.com/121589466/210334271-8465ce68-113e-43c4-9f59-eac06f4d1a27.png)  
You can now enter a new default password for them. Make sure “user must change password at next logon” is selected. You should also check “unlock the users account” to make sure its unlocked if the user tried too many times to logon. Then hit apply.  
![image](https://user-images.githubusercontent.com/121589466/210334297-5d0634cf-7419-494d-be25-1e44b55e6621.png)  

4.	Disable accounts  
When a user leaves the organization or has their machine compromised, you will need to disable their account. To do so, right click on their user profile and select Reset Password.  
![image](https://user-images.githubusercontent.com/121589466/210486758-7582dbc0-0430-439f-bcdd-aeeaa6b8d873.png)  

5.	Create and structure Organizational Units
Having the structure of your Organizational Units setup properly will make a huge difference in how difficult it is to manage user permissions and configure group policy. It’s best to structure your Organizational Units to reflect the physical structure of the organization. You will also want your structure to be as simple and minimal as possible. Too many Organizational Units will make it difficult and confusing to manage.

Let’s go through how to setup a typical Organizational Unit tree from scratch. First, you will right click on the domain and select new -> Organizational Unit.  
![image](https://user-images.githubusercontent.com/121589466/210486792-d3e3013e-ac04-4e46-a47e-2d533bca6fb5.png)  
This new O.U will be the parent container that represents the overall business organization. Its best to also add an underscore in front of the name (ex: _Production). This will make it appear at the top of the list of Organizational Units in the domain structure.  
![image](https://user-images.githubusercontent.com/121589466/210486825-3c1697be-1cda-4cf4-b35a-4a2db397a448.png)  
Next, you will create Organizational Units that represent different physical locations of the business. Within those locations you can then create further sub-divisions for each floor or section of each location. 
 
Within those physical divisions, you can then create Organizational Units that represent different departments on each floor. Within each department, you can then create a final Organizational Unit for the managers of those departments.
If your organization is only in one location or just has one floor, you can skip those layers and only add the subdivisions that make sense for your organization. 
 
You can now drag the users into the appropriate Organizational Units to finalize the structure of your organization. You can also right click on a user and select Move. 
  
Now you can select which O.U to move that user into.
 

6.	Configure and update group policy
Now that you have setup the structure of your Organizational Units and added the right users to them, you can now configure group polices.

a.	Custom wallpaper 
The classic group policy example is to enforce a custom wallpaper for an entire department. You will do this for the I.T department. To do this, go to the Group Policy Management tool.
 
Right click on the Organizational Unit that you want to add a policy to. Then select “Create a GPO in this domain, and Link it here…”.
 
Give it a name that will make it easy to understand what this policy is doing. 
 
The new Group Policy Object (GPO) will appear under the Organizational Unit it is created for. To customize the GPO, right click the GPO and select Edit. 
 
This will bring up the Group Policy Management Editor. Navigate to the policy that you want to make changes to. To change the wallpaper, navigate through the folders on the left and go to User Configuration -> Administrative Templates -> Desktop -> Desktop. Then on the right. Double click on Desktop Wallpaper.
 
You can now select the Enabled radio button on the upper left. This will now allow you to enter the path to the image that you want to use for the wallpaper. Also change the wallpaper style to Fill. Then hit apply. The next time a user in the I.T Organizational Unit logs in, they will see the new wallpaper.
 
For this lab, you can use one of Microsoft’s built-in wallpapers. They are located here: C:\Windows\Web\Wallpaper.

Its best to place the wallpaper image in a shared folder. This will allow any computer on the network to reference the image file.

To create a shared folder; right click in the desired location and select New -> Folder.
 
Name that folder IT Wallpaper. Then right click on it and select Properties.
 
Click on the Sharing tab then click on the Advanced Sharing button.
 
Check the Share this folder box. Give the share a name. Then click on the Permissions button.
 
Make sure that the only permission for everyone is Read. Then click ok. Then hit Apply.
 
You will now go back to the sharing tab for the folder. You can now copy the network path and paste it into the GPO path. 
 
You will also need to append the wallpapers image name to the shared folder path.
 
You can also make sure only users that are part of the domain can access this shared folder. Right click on the shared folder and go to properties. Then go to the security tab. Click the edit button.
 
Then click on Add.
 
Type in Authenticated Users the click Check Names.
 
You can now click ok to apply the changes.
You will leave this group with the default permissions. Click apply to finalize the changes.
 

b.	Install google chrome on all user machines in a department.
It’s common to pre-install certain software onto client computers. This allows the organization to have pre-approved software installed on client machines. 
In this example, you will install Google Chrome on all client machines in the sales department. 

You will first have to download the .msi version of Google Chrome. The .exe version will not work. You can also use 3rd party software to convert .exe files to .msi.

To get the .msi version, you will have to download the enterprise version of Google Chrome. You can find it by searching on Google for “google chrome for enterprise msi”. The direct link to it is here: https://chromeenterprise.google/browser/download/

After you download Chrome Enterprise, you will need to create a new OU that will contain the machines that you want Chrome to be installed on. This is because all new machines are added under the Computers folder by default. This is a folder and not an OU so you are not able to create a GPO that will be able to target that folder. Its best practice is to create this OU of machines next to the OU that contains those Users. It will look similar to the example below.
 
After creating the OU for the machines, drag the desired machines from the Computers folder into this new OU.
 
You will also need to create a shared folder to store the Chrome installation file while still making it accessible to other computers on the network. To create a shared folder, right click in the desired location and select New -> Folder.
 
Name that folder “IT Dept Chrome Install”. Then right click on it and select Properties.
 
Click on the Sharing Tab then click on the Advanced Sharing button.
 
Check the Share this folder box. Give the share a name. Then click on the Permissions button.
 
Make sure that the only permission for everyone is Read. Then click ok. Then hit apply.
 
You can also make sure only users that are part of the domain can access this shared folder. Right click on the shared folder and go to Properties. Then go to the Security tab. Click the edit button.
 
Then click on add.
 
Type in Authenticated Users the click Check Names.
 
You can now click ok to apply the changes.
You will leave this group with the default permissions. Click apply to finalize the changes.
 
To get the link to the shared folder. Right click on it and select Properties. Under the Sharing tab, you will see the network path. You will also have to append the name of the installation file to the end of this path. EX: \\DCSERVER\IT Dept Installs\Chrome\GoogleChromeStandaloneEnterprise64.msi
 
Now you are ready to create the GPO. Go to Server Manager and open the Group Policy Manager tool.
 
Right click on the Organizational Unit that you want to add a policy to. Then select “Create a GPO in this domain, and Link it here…”.
 
Give it a name that will make it easy to understand what this policy is doing. 
 
The new Group Policy Object (GPO) will appear under the Organizational unit it is created for. To customize the GPO, right click the GPO and select Edit. 
 
This will bring up the Group Policy Management editor. Navigate to the policy that you want to make changes to. To add our entry. Go to Computer Configuration -> Policies -> Software Settings -> Software installation. Right click on Software installation and select Properties.
 
You can now paste the location of the shared folder (the folder but not the installation file path) under Default package location. Then click apply. Then ok.
 
Now right click again on Software installation and select New -> Package. 
 
This will open the location of the shared folder that you provided earlier. You can then navigate to and click on the installation file and select open.
 
Then select Assigned and click ok.
 
You will now see Google Chrome show up in the panel.
 
Now the next time the user logs into that client computer they will have Google Chrome installed. If you don’t see Chrome installed on the client machine then you might have to wait a few minutes for it to finish installing. You can also execute the command gpupdate /force to update the group policy on that machine. Then restart that machine again to see if Chrome has been installed. 

c.	Map network drive using group policies.
Having one common drive which only users in a single department can access is a common scenario. This is useful as a central repository where everyone in that department can store and find files to get their job done. 

To map a network drive; you will first have to create a security group which will contain a list of all users which can access this network drive. Create the security group by going to Active Directory Users and Computers. Right click in the OU that you want to create the new security group inside. Select New -> Group.
 
Give the Group a name and select ok.
 
You can now add members to this security group. Select the users you want to add then right click and select Add to a group.
 
Then enter the name of the group and clicking Check Names to confirm the group name. Then selecting ok to add those users to the group.
 
You can confirm these users are in the group by right clicking on the security group and selecting Properties. Then navigate to the Members tab to confirm they are listed there. You can add additional users by selecting Add. Now you can search and add more users to the group if needed.
 
You will need to also create a shared folder which will become our mapped drive. You do this by right clicking where you want this shared folder to be and selecting New -> Folder. 
 
Give it a name then right click and select Properties.
 
Go to the Sharing tab and select Advanced Sharing.
 
Then check the Share this folder box. Also give the share a name. Now click the Permissions button.
 
Click the Add button.
 
Type in Authenticated Users then click the Check Names button to confirm. Then select ok and apply.
 
Make sure the permissions for Authenticated Users are set to Change and Read. Now select ok and then apply. 
 
You can also make sure only users that are part of the domain can access this shared folder. Right click on the shared folder and go to Properties. Then go to the Security tab. Click the Edit button.
 
Then click on Add.
 
Type in Authenticated users then click Check Names. You can now click ok to apply the changes.
 
You will leave this group with the following permissions. Click apply to finalize the changes.
 
Take note of the path of the shared folder for later.  
You can now move onto creating the GPO. Go to Server Manager and open the Group Policy Management tool.
 
You will now create the GPO in the OU that contains your Security Group. Right click on that OU and select “Create GPO in this domain and link it here”. 
 
Give the GPO a name that makes sense. Then select ok.
 
Now right click on the GPO and select Edit.
 
This will open the Group Policy Management Editor. Navigate to User Configuration -> Preferences -> Drive Maps. Right click on Drive Maps and select New -> Mapped Drive.
 
Change Action to Create. Then add the path for the shared folder that you created earlier. Add the name of the drive under Label as.  Then check the Use radio control and select your desired drive letter.
 
Next select the Common tab. Check the Run in logged-on users security context and Item level targeting box. Then click the Targeting box.
 
Now select on New Item then Security Group.  This will allow you to specify that you only want users in a certain security group to have access to this drive.
 
Select the button with three dots on the right to find the specific security group.
 
Enter the name of the group and then select Check Names to confirm the name. Then select ok.
 
You will now see the conditions update. Now select ok, apply then ok again to apply changes.
 
Now your changes should be seen in Group Policy Management Editor.
 
Now you can test the new drive by logging in as a user in the specified security group. If the drive does not show-up then you can enter the command “gpupdate /force” then restart the machine.
You will also want to test that users in that security group have access to write and read to that drive. Also make sure that other users outside of that security group can’t access this drive.

Other Common Tasks
Other tasks include ways to remotely troubleshoot a client machine.
1.	Remotely logging into machines using Remote Desktop Protocol (RDP)

To use RDP, you will first need to enable it on the target computer. Open the Settings app and go to System -> About. Then scroll down and click on Advanced system settings. You will be prompted to enter an administrator username and password.
 
Go to the Remote tab. Then click on Allow Remote Connections to this computer. Then click apply then ok.
 
Now you can go back to your admin machine and try to RDP into the client machine. To do this, open the Remote Desktop Connection app. Click Show Options to expand the page. Enter the machine’s name including the domain name as shown below. Also enter the admin username that you want to logon with. Then click connect and enter the password to that account. 
 
If a user is logged in on that machine, you will see a prompt asking you if you want to proceed and log that user off.
 
On the user end. They will see the following prompt. They have the option to allow or disallow the RDP connection.
 
You will know you are in a RDP session by looking at the top of your screen. You will see the name of the machine that you are connected to. You can exit the session by clicking the X on the right or signing out of the machine.
 

2.	Remote Assistance
RDP is useful for performing tasks on a user’s machine but it’s very disruptive. It forces the user to log off and they could potentially lose progress on their work. You can avoid this by using Remote Assistance. This allows you to remotely control a user’s machine.

To setup Remote Assistance, you will first need to enable it on the controlling computer. Go to sever manager and click Add Roles and Features.
 
Click next until you get to the features page. Check the box for Remote Assistance. Then continue to click next to the end to complete the installation.
 

Now you can create a GPO that will restrict access to only allow users in a certain security group to perform Remote Assistance. This will typically be the users who are in the IT OU and work as helpdesk.

To create the security group, Right click on the OU you want to create the security group in and select New -> Group. Give it a name that will be easy to understand later.
 
Now you can add users from the IT OU who have permission to use Remote Assistance. You can select those users and right click and select Add to group. 
 
Enter the name of the group you created then click Check Name to confirm. Then select ok.
 

With the security group created and the members added to it. You can now create the GPO. To create the GPO, go to Server Manager and go to Tools -> Group Policy Management. 
 
Navigate to the Group Policy Objects folder and right click and select New. Then give it a name.
 
Right click on the GPO you just created and select Edit.
 
Navigate to Computer Configuration -> Policies -> Software settings -> Administrative Templates -> System -> Remote Assistance. Click on Remote Assistance. Then double click Configure Offer Remote Assistance.
 
Click the Enabled radio button. Also make sure the Allow helpers to remotely control the computer is selected. Then Click the Show button.
 
Enter the name of the security group you create earlier. Then click apply then ok to finish editing the GPO.
 

Next, depending on your system, you might need to create a firewall rule to allow this connection to the client machine. Go back in the Remote Assistance GPO and navigate to Computer Configuration -> Policies -> Windows Settings -> Security Settings -> Windows Firewall with Advanced Security -> Windows Firewall with Advanced Security -> Inbound Rules. Right click on Inbound Rules then select New Rule.
 
Click the Predefined radio button. Then select Remote Assistance from the drop-down menu.
 
Check the two rules below. Then click next.
 
Then click allow the connection. Then click finish.
 

Now you can open remote assistance and try to connect to the user’s machine. 
To do this, first click the windows start button and type in Remote Assistance. Click on the result “invite someone to connect to your PC and help you”.
 
Now click on “Help someone who has invited you”.
 
At the bottom, click on Advanced connection option for help desk.
 
Now you can type in the machine name or IP address of the target machine. Then click next.
 
On the client’s machine, they will see the window below. When the user clicks yes, then you will be able to take control of their computer.
 
You can request control of the client machine by clicking Request control.
 
The user will have to click yes to the window below to allow you to take control of their machine.
 

Sometimes for security reasons, it might be company policy that users are the ones to initiate the remote assistance. To do this, the client will have to click the windows start button and type in remote assistance. Click on the result “invite someone to connect to your PC and help you”.
 
Now click on “Invite someone you trust to help you”.
 
 Then click “Save this invitation as a file”
 
Save the file to your desktop then click ok. 
 
The following window will open and show the password to the Remote Assistance invite. The user can now send this file to the admin to get remote assistance.
 
You can also type \\%ClientName%\C$ in file explore to access their C drive. Then navigate to users -> ClientName -> desktop. Then you can open the file yourself. Then you can ask the user to tell you the password over the phone.
 



Notes:
This lab was inspired by the home lab video created by Josh Makador. https://www.youtube.com/watch?v=MHsI8hJmggI
