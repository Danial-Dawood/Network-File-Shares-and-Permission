# <h1>Network File Shares & Permissions</h1>
<h2>In this lab we will practice how to share files over the network and how to give certain users certain permissions </h2>
<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Command Prompt

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)
<h2> Deployment and Configuration Steps</h2>
<p></p>

- Item 1 - Log into the windows 10 vm with one of the random users(not a admin)
- Item 2 - Go to the Windows Server VM and create 4 folders in the C-Drive, name them read-access, write-access, no-access and accounting
- Item 3 - For all of these folders they will be shared on the network and then their permissions need to be set the permission their name states
- Item 4 - So for "Read Access" after making the folder right click it and go to properties, then click on sharing then on the line write in 'domain users' then click add. As you can see when typing that in and clicking add, it populates into the box above the name of the user you made to sign in. This will give any one of the users we made the ability to read what is in that folder but that is all.(also you can see inside the box to the right of domain users that is how we set the permsissions when we share a file over the networksince its already at read I didnt need to change it <img width="1440" alt="Screen Shot 2023-11-01 at 11 21 38 PM" src="https://github.com/Danial-Dawood/Network-File-Shares-and-Permission/assets/149525309/b4629592-7cdf-43ac-be38-ee22a05719b4">
- Item 5 - Do the same thing for the Write-Access folder exact change the permission to read and write(real world tip after sharing and setting the permissions it give you the file path so just enter that into another computer on the same V-Net and it will lead you directly there \\DC-1\Write-Access) <img width="1440" alt="Screen Shot 2023-11-01 at 11 27 34 PM" src="https://github.com/Danial-Dawood/Network-File-Shares-and-Permission/assets/149525309/e13fb509-2f09-4aab-a7f4-5797514d7365">
- Item 6 - So for the 'No-Access' folder its not gonna be the exact same as the other two once we open up the sharing tab instead of entering domain users into the box we will be entering domain admins. This means that all normal users are not going to have access to even open the folder only admins will be able to.Give the Admins the ability to Both read and write <img width="1440" alt="Screen Shot 2023-11-01 at 11 34 32 PM" src="https://github.com/Danial-Dawood/Network-File-Shares-and-Permission/assets/149525309/81c386fe-cdb5-43ae-8a27-b24096bf226e"> (For right now leave the accounting folder alone)
- Item 7 - As you can see typing in \\DC-1 will bring up all the folders we just got done sharing.<img width="1440" alt="Screen Shot 2023-11-01 at 11 40 16 PM" src="https://github.com/Danial-Dawood/Network-File-Shares-and-Permission/assets/149525309/4f11baad-ff0f-43e9-aecf-82f6e4460b50"> We can go through there folders and if everything was done correctly we will be able to Open the 'Read-Access' Folder but not make anything inside it. As Well as we wont be able to Create inside the 'Write-Access', and finally we shouldnt be even able to go into the 'No-Access' Folder because of the fact that we are not logged in on a admin account.
- Itme 8 - Now for the accounting folder, for this we going to make a security group for accounting and assign permissions so that only if youre in the accounting group will you be able to see/read/write on this folder. So we will go into the VM that is running Windows Server, and make a new orginational unit and label it _SECURITYGROUPS. Open that folder up right click the center on the screen and create new group and lebel the group Accounting(make sure you label this the same as the group name.)Then go back to the file mamager and share the accounting folder with the accounting group and give them permission to read and write. <img width="1440" alt="Screen Shot 2023-11-01 at 11 55 28 PM" src="https://github.com/Danial-Dawood/Network-File-Shares-and-Permission/assets/149525309/59a279a1-4d08-4f98-bfab-20fa5ff7db1f">
- Item 9 - Now going into the VM with windows 10 if we click the accounting folder we dont have access to it because we have no assigned our random domain user to the accounting group. So go back onto the windows server vm and go to _SECURITYGROUPS orginational unit we had made and click accounting and the click members and then add the user name for the user that your currently logged into for the windows 10 vm. (which for me is bapofa.hagaxe, once you log off and log back in you will be able to access the accounting folder) As you can see after logging off and back in i can n ow access the folder<img width="1440" alt="Screen Shot 2023-11-02 at 12 08 56 AM" src="https://github.com/Danial-Dawood/Network-File-Shares-and-Permission/assets/149525309/d5dcaf17-584b-4da2-b98b-0d71bdad1e21">



