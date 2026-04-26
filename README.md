<p align="center">
<img width="1508" height="836" alt="image" src="https://github.com/user-attachments/assets/d1501ed3-f9d1-458b-857a-56fa79402271" />

</p>

<h1>osTicket - Prerequisites and Installation</h1>
In this lab, I set up osTicket from scratch using the required installation files. Several preparatory steps must be completed before installing the ticketing system. The lab is performed on a Windows 10 Pro virtual machine hosted on Azure, and all referenced installation files can be found at the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">link provided!</a><br />


<h2>Environments and Technologies Used</h2>

- Remote Desktop Connection
- Microsoft Azure (Virtual Machines/Compute)
- MySQL
- Internet Information Services


<h2>Operating Systems Used </h2>

- Windows 10 Pro</b>


<h2>Installation Steps</h2>

<p>
<img width="1224" height="702" alt="image" src="https://github.com/user-attachments/assets/25808b91-4fed-42a8-97e2-547ba5429d63" />

</p>
<p>
Before installing any files, you need to enable Internet Information Services (IIS), since osTicket requires IIS to run locally. To do this, open the Control Panel, then go to Programs and select “Turn Windows features on or off.” In that window, expand Internet Information Services, then expand Web Management Tools and check IIS Management Console. Next, expand World Wide Web Services, then Application Development Features, and enable CGI. Click OK to apply the changes.
</p>
<br />

<p>
<img width="1507" height="771" alt="image" src="https://github.com/user-attachments/assets/79346114-879c-4f0f-91a8-46b3fe472d9e" />

</p>
<p>
Once IIS is enabled, download and install PHP Manager for IIS (PHPManagerforIIS_V1.5.0.msi) from the installation files folder. After that, proceed to download and install the Rewrite Module (rewrite_amd64_en-US.msi).
</p>
<br />

<p>
<img width="1508" height="776" alt="image" src="https://github.com/user-attachments/assets/8f53bc35-254a-43bd-a08b-a8ae63e238ee" />

</p>
<p>
Once the Rewrite Module is installed, create a new directory named C:\PHP on the Windows (C:) drive. This directory will be used to hold the extracted files from the PHP 7.3.8 archive (php-7.3.8-nts-Win32-VC15-x86.zip) downloaded from the installation files. Unzip the archive and place all of its contents into the C:\PHP folder.
</p>
<br />

<p>
<img width="1512" height="765" alt="image" src="https://github.com/user-attachments/assets/e1c6045b-a4d6-400e-a24d-23b2ded5d8a5" />

</p>
<p>
Next, download and install VC_redist.x86.exe from the installation files folder.
</p>
<br />

<p>
<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/f73dbd14-f3e0-4fd2-aae0-bd907e393e20" />

</p>
<p>
Next, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the installation files. During the setup process, accept the license agreement, choose the Typical installation option, and proceed with the install. Once installation is complete, open the Configuration Wizard. Select Standard Configuration, enable the option to install MySQL as a Windows Service, and ensure that the server is set to launch automatically. When prompted for credentials, use root as the username and Password1 as the password. While real-world environments should use stronger, less predictable credentials, these defaults are sufficient for this lab.
</p>
<br />

<p>
<img width="1509" height="770" alt="image" src="https://github.com/user-attachments/assets/8e3030f3-ea69-4566-bb7b-009793ad14d3" />

</p>
<p>
Next, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the installation files. Within the MySQL setup wizard, click "I agree" and select a Typical install and Install. Launch the Configuration Wizard after the installation. Select Standard Configuration and select Install As Windows Service and make sure Launch the MySQL Server automatically is checked. For credentials, the username will be root and the password is Password1. In a practical setting, the credentials will be decided by the user. For the purposes of this lab, the standard credentials root and Password1 will do.
</p>
<br />

<p>
<img width="1513" height="771" alt="image" src="https://github.com/user-attachments/assets/6f6725dc-32ea-4e21-b381-d30a0030a489" />

<img width="1511" height="777" alt="image" src="https://github.com/user-attachments/assets/c4e6f79f-1866-4ff3-9bc8-c50689f239f4" />

</p>
<p>
Before installing osTicket, you first need to configure settings in IIS. Launch IIS with administrative privileges and open PHP Manager. From there, click “Register new PHP version,” then browse to the PHP folder you created earlier and select the php-cgi.exe file. Once the PHP version is registered, restart the IIS server through the management console to apply the changes.
</p>
<br />

<p>
<img width="1509" height="772" alt="image" src="https://github.com/user-attachments/assets/f8b37048-f9db-417c-8296-28593713a226" />

</p>
<p>
Download osTicket v1.15.8 from the installation package. After extracting the files, copy the “upload” folder into the directory c:\inetpub\wwwroot. Once it’s in place, rename the “upload” folder to “osTicket.” When finished, restart the IIS server to ensure the changes take effect.
</p>
<br />

<p>
<img width="1509" height="773" alt="image" src="https://github.com/user-attachments/assets/4529ff3a-79e6-4fad-82b3-cec4d9ed1e42" />

<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/b3ddabbf-b162-4ee5-ba74-13fa36643043" />

<img width="1226" height="673" alt="image" src="https://github.com/user-attachments/assets/4fd61a4a-1ecd-412b-a602-1a18a0265df4" />

</p>
<p>
In the IIS console, go to Sites, then Default, and select osTicket. Click “Browse *:80” to open the osTicket installation page. You may see that some required extensions are not enabled yet. To address this, open PHP Manager within the osTicket section of IIS and select “Enable or disable an extension.” Then enable the following extensions: php_imap.dll, php_intl.dll, and php_opcache.dll.
</p>
<br />

<p>
<img width="1509" height="778" alt="image" src="https://github.com/user-attachments/assets/02937383-0071-4ef1-8e9c-089ba59df4a2" />

<img width="1508" height="776" alt="image" src="https://github.com/user-attachments/assets/15df5dd0-2cb7-4453-b99e-ba08791480a9" />

</p>
<p>
Before proceeding with the osTicket installation, you’ll need to rename a file and update its permissions. In the directory C:\inetpub\wwwroot\osTicket\include, rename ost-sampleconfig.php to ost-config.php. Then, open the Properties for the new ost-config.php file and adjust its permissions by disabling inheritance, removing all existing entries, and adding a new permission that grants Everyone full access.
</p>
<br />

<p>
<img width="1528" height="837" alt="image" src="https://github.com/user-attachments/assets/a5356255-b5a5-4451-a6ae-45ff059e74f4" />

<img width="1525" height="837" alt="image" src="https://github.com/user-attachments/assets/267fb51b-37bc-47c0-a8ec-2e798f8c3db7" />

</p>
<p>
Download and install HeidiSQL from the provided installation files. After launching it, set up a new session and enter the MySQL password you created earlier. Once connected, right-click on “Unnamed” and create a new database called osTicket. 
</p>
<br />

<p>
<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/ee667e4a-f4f8-43d2-8370-f40a8d2bae23" />

</p>
<p>
In the osTicket browser window, fill in the required information to complete the setup. When prompted for the MySQL database details, use the same credentials you configured for MySQL and in HeidiSQL.
</p>
<br />

<p>
<img src="https://i.imgur.com/3nczMAD.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/7V2YmH6.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Once the installation is complete, osTicket should be up and running. Before you start using it, perform a bit of cleanup. Begin by deleting the setup folder located in C:\inetpub\wwwroot\osTicket. Then go back to C:\inetpub\wwwroot\osTicket\include and update the permissions for the ost-config.php file. Remove the full access granted to Everyone and set the permissions back to read-only. 
</p>
<br />

<h2>osTicket Installed!</h2>

osTicket is now installed and ready for use. I used this setup to learn how ticketing systems operate and how to handle and resolve support requests. In IT support roles, working with a team to address users’ technical issues through a ticketing system is essential. This lab provided hands-on experience building a ticketing system from scratch and helped establish a foundation for the work I’ll be doing in the future.
