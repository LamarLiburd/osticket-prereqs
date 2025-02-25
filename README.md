<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />



<h2>Environments and Utilities Used</h2>

- Microsoft Azure 
- Remote Desktop
- Internet Information Services (IIS)
- Heidi SQL
<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Project Walk-through</h2>

1.) First, go to [https://portal.azure.com/] (https://portal.azure.com/) to create a virtual machine. Set it up with Windows 10 Pro, version 22H2. Make sure the virtual machine has at least 2 vCPUs and 16 GB of memory.

2.) Once your virtual machine is created, connect to it using the **public IP address** assigned to the VM. Use the **Remote Desktop Connection** app to establish the connection.
</p>
<br />

<p>
<img src="https://i.imgur.com/MAhXK2e.png" alt="Disk Sanitization Steps" style="max-width: 80%; height: auto;">

</p>
<p>
<p>
<img src="https://i.imgur.com/Zf2jw07.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
3.) Once connected to your virtual machine, go into your Control Panel, open Programs, and select Turn Windows Features On or Off.

<p>
<img src="https://i.imgur.com/fGXMpx4.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
<p>
<img src="https://i.imgur.com/LBGkAw6.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
4.) You will want to install/enable IIS in Windows with CGI and Common HTTP Features
- World Wide Web Services -> Application Development Features ->
[X] CGI
[X] Common HTTP Features
<p>
<img src="https://imgur.com/6Y6VzZH.png" height="80%" width="80%" alt="Setting Up in Azure"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/pbPeHb1.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
To ensure the IIS is installed/enabled, go to the internet browser and search for 127.0.0.1 also known as the "loopback IP".
It should look something like this:
<p>
<img src="https://imgur.com/XdKGpGl.png" height="80%" width="80%" alt="Setting Up in Azure"/>
</p>
<p>
5.)With IIS enabled, download and install **PHP Manager for IIS** (*PHPManagerForIIS_V1.5.0.msi*) from the installation files, then follow the installation wizard to complete the setup.
6.) Next from the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)
7.) Create a folder in the C drive called PHP.
8.) From the installation files, download **PHP 7.3.8** (*php-7.3.8-nts-Win32-VC15-x86.zip*) and extract its contents into **C:\PHP**.  

If a warning appears, select **"Keep"** to proceed.
<p>
<img src="https://i.imgur.com/xZv1Yhw.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
<p>
<img src="https://i.imgur.com/YwBhqo0.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>

9.) After downloading and extracting the ZIP file into the **PHP** folder on the **C:** drive, download and install Microsoft C++ from the installation files. Follow the setup wizard to complete the installation.
<img src="https://imgur.com/SocF97p.png" height="80%" width=80% alt="Setting Up in Azure"/>

10.) Download and install MySQL
<img src="https://imgur.com/dFdQagT.png" height="80%" width="80%" alt="Setting Up in Azure"/>

Run the setup wizard:
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->

Make the new root password: Password1
<p>
<img src="https://imgur.com/SeJVW6M.png" height="80%" width="80%" alt="Setting Up in Azure"/>

</p>
<p>

</p>
<p>
11.) Now that we have the files downloaded and installed we will want to search for IIS in the Windows search bar. Open IIS as an Admin.
<p>
<img src="https://imgur.com/gFmrka6.png" height=80% width=80% alt="Setting Up in Azure"/>

</p>
<p>
12.) We will now want to register PHP from within IIS.
<p>
<img src="https://imgur.com/nlD4F1L.png" height="80%" width="80%" alt="Setting Up in Azure"/>
</p>
<p>
  
Restart the IIS server.
<p>
<img src="https://imgur.com/F83Qw2a.png" height="80%" width="80%" alt="Setting Up in Azure"/>
</p>
<p>
13.) Install osTicket 
-Download osTicket from the Installation Files Folder
-Extract and copy the "upload" folder to c:\inetpub\wwwroot
-Within c:\inetpub\root, Rename "upload" to "osTicket"
  <img src="https://imgur.com/op4Cs2g.png" height="80%" width="80%" alt="Setting Up in Azure"/>

Reload IIS again.
 On IIS go to Sites> Default > osTicket
-On the right, click “Browse *:80”
<p>
<img src="https://imgur.com/JnqQOJD.png" height="80%" width="80%" alt="Setting Up in Azure"/>
</p>
<p>
Some extensions are not enabled on the osTicket browser.
<p>
<img src="https://i.imgur.com/eJIsGTn.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
To enable the extensions:  

1. Open **IIS** and navigate to **Sites → Default → osTicket**.  
2. Double-click **PHP Manager**.  
3. Select **"Enable or disable an extension."**
<img src="https://i.imgur.com/vvTLNBH.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
<p>
<img src="https://i.imgur.com/uigyKjb.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
We will want to enable three extensions from here.
1.) php_imap.dll
2.) php_intl.dll
3.) php_opcache.dll
<p>
<img src="https://i.imgur.com/cOem7Nb.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
15. Once those extensions are enabled in IIS, the next step is to rename a file in the **osTicket** folder.  

1. Open **File Explorer** and navigate to:  
   **C:\inetpub\wwwroot\osTicket\include\ost-sample config.php**  
2. Rename **ost-sampleconfig.php** to **ost-config.php**.  
3. Right-click the renamed file and select **Properties**.  
4. Go to the **Security** tab, click **Advanced**, and disable inheritance.  
5. Choose to **remove all inherited permissions** from this object.  
6. Click **Add** to set new permissions.
<p>
<img src="https://i.imgur.com/VPZvOdo.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
Select a principal
<p>
<img src="https://i.imgur.com/PoGk34d.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
Type "Everyone" in the box.
<p>
<img src="https://imgur.com/F4H3ppM.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
Make sure "Full Control" and all other checkboxes are selected.
<p>
<img src="https://imgur.com/rbbGqwB.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click Apply and Ok.
<p>
<img src="https://i.imgur.com/saRO3y5.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
Once complete, continue setting up **osTicket** in the browser. Click **Continue** and fill out the required fields, except for **Database Settings**—we’ll handle that later.
Next, download and install **HeidiSQL** from the installation files.
<p>
<img src="https://i.imgur.com/i7a4gWC.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
Once the program is open, we will create a new session.
<p>
<img src="https://i.imgur.com/g5M1i61.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

<p>
Be sure the username is set to **root** and the password to **Password1**.
<p>
<img src="https://i.imgur.com/LEAZNOc.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
After connecting to the session, return to the browser to continue the setup. In **Database Settings**, set the username to **"root"** and the password to **"Password1."**  

Next, create a new database in **HeidiSQL**:  
1. In **HeidiSQL**, right-click on **"Unnamed"** in the left panel.  
2. Select **"Create new" → "Database."**  
3. Name the database **osTicket** and complete the setup.  

After creating the database, go back to the **osTicket** setup page in the browser and enter **osTicket** in the **MySQL Database** field.
<img src="https://i.imgur.com/0rG1AJm.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
The final step is cleanup. Delete the **setup** folder from your system:  

- **Delete:** *C:\inetpub\wwwroot\osTicket\setup*  
  *(Only delete the setup folder—do not remove anything else.)*  

Then, set the **ost-config.php** file permissions back to **"Read" only**.
<img src="https://i.imgur.com/wFr0pkK.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
<p>
<img src="https://i.imgur.com/jsJOPyn.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
The final step is to log in to osTicket through the browser.
<p>
<img src="https://i.imgur.com/uHVdDsx.png" alt="Disk Sanitization Steps" style="max-width: 40%; height: auto;">

</p>
<p>
