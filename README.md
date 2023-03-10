# Active Directory Home Lab [Part 2]
![image](https://jumpcloud.com/wp-content/uploads/2016/07/AD1.png)  

## Common Active Directory Tasks to Learn  
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
<br><br/>
Let’s go through how to setup a typical Organizational Unit tree from scratch. First, you will right click on the domain and select new -> Organizational Unit.  
![image](https://user-images.githubusercontent.com/121589466/210486792-d3e3013e-ac04-4e46-a47e-2d533bca6fb5.png)  
This new O.U will be the parent container that represents the overall business organization. Its best to also add an underscore in front of the name (ex: _Production). This will make it appear at the top of the list of Organizational Units in the domain structure.  
![image](https://user-images.githubusercontent.com/121589466/210486825-3c1697be-1cda-4cf4-b35a-4a2db397a448.png)  
Next, you will create Organizational Units that represent different physical locations of the business. Within those locations you can then create further sub-divisions for each floor or section of each location.   
![image](https://user-images.githubusercontent.com/121589466/210487037-f6633f04-ab26-4902-97ca-ddf31c3de6ee.png)  
Within those physical divisions, you can then create Organizational Units that represent different departments on each floor. Within each department, you can then create a final Organizational Unit for the managers of those departments.
If your organization is only in one location or just has one floor, you can skip those layers and only add the subdivisions that make sense for your organization.  
![image](https://user-images.githubusercontent.com/121589466/210487134-c5ba864a-844a-4d1a-ab88-0f8cdb4eb332.png)  
You can now drag the users into the appropriate Organizational Units to finalize the structure of your organization. You can also right click on a user and select Move.  
![image](https://user-images.githubusercontent.com/121589466/210487160-351f1c35-83d1-4974-a84c-010ea17595c2.png)  
Now you can select which O.U to move that user into.  
![image](https://user-images.githubusercontent.com/121589466/210487182-051e848a-0e3f-43ed-a9fe-c95cc9d94810.png)  

6.	Configure and update group policy  
Now that you have setup the structure of your Organizational Units and added the right users to them, you can now configure group polices.
<br><br/>
 a.	Custom wallpaper  
 The classic group policy example is to enforce a custom wallpaper for an entire department. You will do this for the I.T department. To do this, go to the Group Policy Management tool.  
 ![image](https://user-images.githubusercontent.com/121589466/210487215-6f933617-4b41-4ff4-b20b-c806ef254dde.png)  
 Right click on the Organizational Unit that you want to add a policy to. Then select “Create a GPO in this domain, and Link it here…”.  
 ![image](https://user-images.githubusercontent.com/121589466/210487226-206e6b65-a9bb-4451-8c51-0a6e49c8eb9a.png)  
 Give it a name that will make it easy to understand what this policy is doing.  
 ![image](https://user-images.githubusercontent.com/121589466/210487238-5e307ff5-d0b2-4f3c-bd8e-20408d05cbe1.png)  
 The new Group Policy Object (GPO) will appear under the Organizational Unit it is created for. To customize the GPO, right click the GPO and select Edit.  
 ![image](https://user-images.githubusercontent.com/121589466/210487251-6efde6e2-dbe0-4317-a36c-722de553a399.png)  
 This will bring up the Group Policy Management Editor. Navigate to the policy that you want to make changes to. To change the wallpaper, navigate through the folders on the left and go to User Configuration -> Administrative Templates -> Desktop -> Desktop. Then on the right. Double click on Desktop Wallpaper.  
 ![image](https://user-images.githubusercontent.com/121589466/210487270-bf39ee9a-a4ea-466d-8164-5149a61ac33c.png)  
 You can now select the Enabled radio button on the upper left. This will now allow you to enter the path to the image that you want to use for the wallpaper. Also change the wallpaper style to Fill. Then hit apply. The next time a user in the I.T Organizational Unit logs in, they will see the new wallpaper.  
 ![image](https://user-images.githubusercontent.com/121589466/210487294-82113190-7d4e-476e-929d-c3b7ba58e9e2.png)  
 For this lab, you can use one of Microsoft’s built-in wallpapers. They are located here: C:\Windows\Web\Wallpaper.
 <br><br/>
 Its best to place the wallpaper image in a shared folder. This will allow any computer on the network to reference the image file.
 <br><br/>
 To create a shared folder; right click in the desired location and select New -> Folder.  
 ![image](https://user-images.githubusercontent.com/121589466/210487350-93d28384-cfd0-4daf-8615-89252e2db676.png)  
 Name that folder IT Wallpaper. Then right click on it and select Properties.  
 ![image](https://user-images.githubusercontent.com/121589466/210487367-e136be40-1e80-4980-b57c-147c2f415117.png)  
 Click on the Sharing tab then click on the Advanced Sharing button.  
 ![image](https://user-images.githubusercontent.com/121589466/210487375-b3d428c6-1ea1-4bc9-aa59-429def3e66ea.png)  
 Check the Share this folder box. Give the share a name. Then click on the Permissions button.  
 ![image](https://user-images.githubusercontent.com/121589466/210487410-adb0902b-26cd-4df0-bc16-6f0f460b8acf.png)
 <br><br/>
 Make sure that the only permission for everyone is Read. Then click ok. Then hit Apply.  
 ![image](https://user-images.githubusercontent.com/121589466/210487634-9f47dd9c-a9c7-44e3-b7fb-3214adc24bb3.png)  
 You will now go back to the sharing tab for the folder. You can now copy the network path and paste it into the GPO path.  
 ![image](https://user-images.githubusercontent.com/121589466/210488484-d192f406-197c-4599-90ac-b0188a4e9b33.png)  
 You will also need to append the wallpapers image name to the shared folder path.  
 ![image](https://user-images.githubusercontent.com/121589466/210488500-16a11e7f-628e-4bac-9ab3-10cc874807c4.png)  
 You can also make sure only users that are part of the domain can access this shared folder. Right click on the shared folder and go to properties. Then go to the security tab. Click the edit button.  
 ![image](https://user-images.githubusercontent.com/121589466/210488516-a779a4d9-b055-445e-984e-83d8496e4590.png)  
 Then click on Add.  
 ![image](https://user-images.githubusercontent.com/121589466/210488536-a41a6d0b-190d-4356-a252-14ea286746f2.png)  
 Type in Authenticated Users the click Check Names.  
 ![image](https://user-images.githubusercontent.com/121589466/210488561-5421b264-5909-4bdc-87ac-ab1a2b6edc2a.png)  
 You can now click ok to apply the changes.
 You will leave this group with the default permissions. Click apply to finalize the changes.  
 ![image](https://user-images.githubusercontent.com/121589466/210488566-8198f950-207c-4d67-a6af-83cf9610f9e6.png)
 <br><br/>
 b.	Install google chrome on all user machines in a department.  
 It’s common to pre-install certain software onto client computers. This allows the organization to have pre-approved software installed on client machines. 
 In this example, you will install Google Chrome on all client machines in the sales department.
<br><br/>
 You will first have to download the .msi version of Google Chrome. The .exe version will not work. You can also use 3rd party software to convert .exe files to .msi.
<br><br/>
 To get the .msi version, you will have to download the enterprise version of Google Chrome. You can find it by searching on Google for “google chrome for enterprise msi”. The direct link to it is here: https://chromeenterprise.google/browser/download/
<br><br/>
 After you download Chrome Enterprise, you will need to create a new OU that will contain the machines that you want Chrome to be installed on. This is because all new machines are added under the Computers folder by default. This is a folder and not an OU so you are not able to create a GPO that will be able to target that folder. Its best practice is to create this OU of machines next to the OU that contains those Users. It will look similar to the example below.  
 ![image](https://user-images.githubusercontent.com/121589466/210488717-601a6390-3da5-4a9c-9573-099fddc70fd5.png)  
 After creating the OU for the machines, drag the desired machines from the Computers folder into this new OU.  
 ![image](https://user-images.githubusercontent.com/121589466/210488723-e30626e4-e13c-4fad-8c73-8d4079676ab6.png)  
 You will also need to create a shared folder to store the Chrome installation file while still making it accessible to other computers on the network. To create a shared folder, right click in the desired location and select New -> Folder.  
 ![image](https://user-images.githubusercontent.com/121589466/210488737-91fbd07f-a1a9-435b-b7e9-c3bcebf3d48d.png)  
 Name that folder “IT Dept Chrome Install”. Then right click on it and select Properties.  
 ![image](https://user-images.githubusercontent.com/121589466/210488747-9b1479a3-6aa5-43c1-a1e1-32a05f30dcb3.png)  
 Click on the Sharing Tab then click on the Advanced Sharing button.  
 ![image](https://user-images.githubusercontent.com/121589466/210488752-9cb24aac-de62-4e62-8a71-064cba020f0b.png)  
 Check the Share this folder box. Give the share a name. Then click on the Permissions button.  
 ![image](https://user-images.githubusercontent.com/121589466/210488766-0a72d2c5-347c-4acd-b8e7-6334a6c1e78b.png)  
 Make sure that the only permission for everyone is Read. Then click ok. Then hit apply.  
 ![image](https://user-images.githubusercontent.com/121589466/210488778-e29227ef-ea95-4858-92c5-807d93255ce2.png)  
 You can also make sure only users that are part of the domain can access this shared folder. Right click on the shared folder and go to Properties. Then go to the Security tab. Click the edit button.  
 ![image](https://user-images.githubusercontent.com/121589466/210488792-555ae9ef-4504-4af2-a014-41ac82f3ddbc.png)  
 Then click on add.  
 ![image](https://user-images.githubusercontent.com/121589466/210488809-2e4cc2fe-4870-4473-96ff-f9e472ee65b8.png)  
 Type in Authenticated Users the click Check Names.  
 ![image](https://user-images.githubusercontent.com/121589466/210488819-49117cbe-2bdf-4c32-8a81-b5ea289d24e4.png)  
 You can now click ok to apply the changes.
 You will leave this group with the default permissions. Click apply to finalize the changes.  
 ![image](https://user-images.githubusercontent.com/121589466/210488829-67866ffd-75ab-41da-acb9-718447399fd4.png)  
 To get the link to the shared folder. Right click on it and select Properties. Under the Sharing tab, you will see the network path. You will also have to append the name of the installation file to the end of this path. EX: \\DCSERVER\IT Dept Installs\Chrome\GoogleChromeStandaloneEnterprise64.msi  
 ![image](https://user-images.githubusercontent.com/121589466/210488850-f8336490-a885-4fe3-b983-7cfa01a6ac46.png)  
 Now you are ready to create the GPO. Go to Server Manager and open the Group Policy Manager tool.  
 ![image](https://user-images.githubusercontent.com/121589466/210488862-9f9fb205-5ce7-40e0-90e2-5a7f691601f5.png)  
 Right click on the Organizational Unit that you want to add a policy to. Then select “Create a GPO in this domain, and Link it here…”.  
 ![image](https://user-images.githubusercontent.com/121589466/210488873-4b5c1e88-9651-40e7-a332-54dcf7e82e2a.png)  
 Give it a name that will make it easy to understand what this policy is doing.  
 ![image](https://user-images.githubusercontent.com/121589466/210488886-0edacc71-db06-4a80-b35b-6279db2ef34d.png)  
 The new Group Policy Object (GPO) will appear under the Organizational unit it is created for. To customize the GPO, right click the GPO and select Edit.   
 ![image](https://user-images.githubusercontent.com/121589466/210488901-f66a4add-d4c2-4323-9f5a-4807668aac4b.png)  
 This will bring up the Group Policy Management editor. Navigate to the policy that you want to make changes to. To add our entry. Go to Computer Configuration -> Policies -> Software Settings -> Software installation. Right click on Software installation and select Properties.  
 ![image](https://user-images.githubusercontent.com/121589466/210488909-2456b98c-fedc-4381-b4fd-8eb9fd43a02f.png)  
 You can now paste the location of the shared folder (the folder but not the installation file path) under Default package location. Then click apply. Then ok.  
 ![image](https://user-images.githubusercontent.com/121589466/210488919-fd713e42-4f24-4d1a-839e-a4f73ebb7360.png)  
 Now right click again on Software installation and select New -> Package.  
 ![image](https://user-images.githubusercontent.com/121589466/210488943-2f998bb2-7100-4c0c-9d7e-26f6f8cd2f22.png)  
 This will open the location of the shared folder that you provided earlier. You can then navigate to and click on the installation file and select open.  
 ![image](https://user-images.githubusercontent.com/121589466/210489003-6b395a30-1cbf-4dee-91d5-7476af79b76b.png)  
 Then select Assigned and click ok.  
 ![image](https://user-images.githubusercontent.com/121589466/210489018-9237b942-39ef-432f-85ee-74699f4ae93d.png)  
 You will now see Google Chrome show up in the panel.  
 ![image](https://user-images.githubusercontent.com/121589466/210489027-7f51fdd7-d444-4dc4-a336-24582efc6c4a.png)  
 Now the next time the user logs into that client computer they will have Google Chrome installed. If you don’t see Chrome installed on the client machine then you might have to wait a few minutes for it to finish installing. You can also execute the command gpupdate /force to update the group policy on that machine. Then restart that machine again to see if Chrome has been installed.
<br><br/>
 c.	Map network drive using group policies.  
 Having one common drive which only users in a single department can access is a common scenario. This is useful as a central repository where everyone in that department can store and find files to get their job done.
<br><br/>
 To map a network drive; you will first have to create a security group which will contain a list of all users which can access this network drive. Create the security group by going to Active Directory Users and Computers. Right click in the OU that you want to create the new security group inside. Select New -> Group.  
 ![image](https://user-images.githubusercontent.com/121589466/210489056-640f0e27-3aac-45d5-90cf-68b8f960ec66.png)  
 Give the Group a name and select ok.  
 ![image](https://user-images.githubusercontent.com/121589466/210489067-47c8e650-b50b-4b7f-946f-5a6cabaa25f1.png)  
 You can now add members to this security group. Select the users you want to add then right click and select Add to a group.  
 ![image](https://user-images.githubusercontent.com/121589466/210489078-aea075ff-6c7d-495b-ac7a-64035367bff7.png)  
 Then enter the name of the group and clicking Check Names to confirm the group name. Then selecting ok to add those users to the group.  
 ![image](https://user-images.githubusercontent.com/121589466/210489087-d1fa1e17-0de3-4cea-a85d-5aa4fa1eafa7.png)  
 You can confirm these users are in the group by right clicking on the security group and selecting Properties. Then navigate to the Members tab to confirm they are listed there. You can add additional users by selecting Add. Now you can search and add more users to the group if needed.  
 ![image](https://user-images.githubusercontent.com/121589466/210489097-00f743c7-ac80-42ae-8509-f7580796454d.png)  
 You will need to also create a shared folder which will become our mapped drive. You do this by right clicking where you want this shared folder to be and selecting New -> Folder.  
 ![image](https://user-images.githubusercontent.com/121589466/210489112-a8e296ab-5fe1-4d86-a958-d13ad61f8bf8.png)  
 Give it a name then right click and select Properties.  
 ![image](https://user-images.githubusercontent.com/121589466/210489125-ca079faa-712f-4940-8f6d-84cddcf1b46e.png)  
 Go to the Sharing tab and select Advanced Sharing.  
 ![image](https://user-images.githubusercontent.com/121589466/210489137-39148823-d44a-4afe-b1ee-6a0f61e61591.png)  
 Then check the Share this folder box. Also give the share a name. Now click the Permissions button.  
 ![image](https://user-images.githubusercontent.com/121589466/210489151-acb281fb-37ca-4f80-93b5-f81a27649d93.png)  
 Click the Add button.  
 ![image](https://user-images.githubusercontent.com/121589466/210489165-39cba4c2-9d24-44fb-b62a-38d2ad96452f.png)  
 Type in Authenticated Users then click the Check Names button to confirm. Then select ok and apply.  
 ![image](https://user-images.githubusercontent.com/121589466/210489182-8ae457e3-29ab-4fed-be7f-7623a2657e55.png)  
 Make sure the permissions for Authenticated Users are set to Change and Read. Now select ok and then apply.   
 ![image](https://user-images.githubusercontent.com/121589466/210489195-1d6f3b81-8dd4-45f3-90ca-b69437f50225.png)  
 You can also make sure only users that are part of the domain can access this shared folder. Right click on the shared folder and go to Properties. Then go to the Security tab. Click the Edit button.  
 ![image](https://user-images.githubusercontent.com/121589466/210489204-0257c9bf-69c6-4983-86b6-05258c65bffa.png)  
 Then click on Add.  
 ![image](https://user-images.githubusercontent.com/121589466/210489213-ee0749d5-e97b-495f-8210-828f306a133a.png)  
 Type in Authenticated users then click Check Names. You can now click ok to apply the changes.  
 ![image](https://user-images.githubusercontent.com/121589466/210489236-c877a66d-977d-43e1-a3cd-9cfef44fd4f6.png)  
 You will leave this group with the following permissions. Click apply to finalize the changes.  
 ![image](https://user-images.githubusercontent.com/121589466/210489242-223284c6-a371-4246-b51a-2a4de948c76f.png)  
 Take note of the path of the shared folder for later.  
 ![image](https://user-images.githubusercontent.com/121589466/210489265-0648fbde-49bb-4afb-a9f1-6e39b29fdfea.png)
<br><br/>
 You can now move onto creating the GPO. Go to Server Manager and open the Group Policy Management tool.  
 ![image](https://user-images.githubusercontent.com/121589466/210489281-b2f395bb-9202-4f14-8f4f-0ebdc092bfea.png)  
 You will now create the GPO in the OU that contains your Security Group. Right click on that OU and select “Create GPO in this domain and link it here”.
<br><br/>
 Give the GPO a name that makes sense. Then select ok.  
 ![image](https://user-images.githubusercontent.com/121589466/210489291-2868ec61-41cb-4a8a-9b3a-f42d193335ae.png)  
 Now right click on the GPO and select Edit.  
 ![image](https://user-images.githubusercontent.com/121589466/210489307-37f74832-b92a-4d01-911b-423d008894fc.png)  
 This will open the Group Policy Management Editor. Navigate to User Configuration -> Preferences -> Drive Maps. Right click on Drive Maps and select New -> Mapped Drive.  
 ![image](https://user-images.githubusercontent.com/121589466/210489323-24dcea44-ee9b-4961-90d2-95014d287cf1.png)  
 Change Action to Create. Then add the path for the shared folder that you created earlier. Add the name of the drive under Label as.  Then check the Use radio control and select your desired drive letter.  
 ![image](https://user-images.githubusercontent.com/121589466/210489334-7c23fcc1-0f95-45e8-be90-3a244c602812.png)  
 Next select the Common tab. Check the Run in logged-on users security context and Item level targeting box. Then click the Targeting box.  
 ![image](https://user-images.githubusercontent.com/121589466/210489342-91415e33-bfc7-493a-9cfd-84f138651bdb.png)  
 Now select on New Item then Security Group.  This will allow you to specify that you only want users in a certain security group to have access to this drive.  
 ![image](https://user-images.githubusercontent.com/121589466/210489350-c9ce5d96-3ab1-49b6-ab12-128fd1136ea3.png)  
 Select the button with three dots on the right to find the specific security group.  
 ![image](https://user-images.githubusercontent.com/121589466/210489361-38f71fb2-8523-4d93-95a8-22973c945b81.png)  
 Enter the name of the group and then select Check Names to confirm the name. Then select ok.  
 ![image](https://user-images.githubusercontent.com/121589466/210489369-21ebcd54-6fc2-4cda-85a9-6084a442b6ef.png)  
 You will now see the conditions update. Now select ok, apply then ok again to apply changes.  
 ![image](https://user-images.githubusercontent.com/121589466/210489384-96938605-ea8e-47be-b658-3d37ecc137f0.png)  
 Now your changes should be seen in Group Policy Management Editor.
<br><br/>
 Now you can test the new drive by logging in as a user in the specified security group. If the drive does not show-up then you can enter the command “gpupdate /force” then restart the machine.  
 You will also want to test that users in that security group have access to write and read to that drive. Also make sure that other users outside of that security group can’t access this drive.  


Notes:  
This lab was inspired by the home lab video created by Josh Makador.  
https://www.youtube.com/watch?v=MHsI8hJmggI  
