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
<img src="https://i.imgur.com/UW2eIpW.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Next, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the installation files. During the setup process, accept the license agreement, choose the Typical installation option, and proceed with the install. Once installation is complete, open the Configuration Wizard. Select Standard Configuration, enable the option to install MySQL as a Windows Service, and ensure that the server is set to launch automatically. When prompted for credentials, use root as the username and Password1 as the password. While real-world environments should use stronger, less predictable credentials, these defaults are sufficient for this lab.
</p>
<br />

<p>
<img src="https://i.imgur.com/UW2eIpW.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Next, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the installation files. Within the MySQL setup wizard, click "I agree" and select a Typical install and Install. Launch the Configuration Wizard after the installation. Select Standard Configuration and select Install As Windows Service and make sure Launch the MySQL Server automatically is checked. For credentials, the username will be root and the password is Password1. In a practical setting, the credentials will be decided by the user. For the purposes of this lab, the standard credentials root and Password1 will do.
</p>
<br />

<p>
<img src="https://i.imgur.com/9ylqXGk.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/KoK1Lug.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Before installing osTicket, you first need to configure settings in IIS. Launch IIS with administrative privileges and open PHP Manager. From there, click “Register new PHP version,” then browse to the PHP folder you created earlier and select the php-cgi.exe file. Once the PHP version is registered, restart the IIS server through the management console to apply the changes.
</p>
<br />

<p>
<img src="https://i.imgur.com/ivQmua0.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Download osTicket v1.15.8 from the installation package. After extracting the files, copy the “upload” folder into the directory c:\inetpub\wwwroot. Once it’s in place, rename the “upload” folder to “osTicket.” When finished, restart the IIS server to ensure the changes take effect.
</p>
<br />

<p>
<img src="https://i.imgur.com/s856Cpz.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/pNkLVo6.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/Mpq7ybU.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
In the IIS console, go to Sites, then Default, and select osTicket. Click “Browse *:80” to open the osTicket installation page. You may see that some required extensions are not enabled yet. To address this, open PHP Manager within the osTicket section of IIS and select “Enable or disable an extension.” Then enable the following extensions: php_imap.dll, php_intl.dll, and php_opcache.dll.
</p>
<br />

<p>
<img src="https://i.imgur.com/CdkPTsv.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/5ggnkk9.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Before proceeding with the osTicket installation, you’ll need to rename a file and update its permissions. In the directory C:\inetpub\wwwroot\osTicket\include, rename ost-sampleconfig.php to ost-config.php. Then, open the Properties for the new ost-config.php file and adjust its permissions by disabling inheritance, removing all existing entries, and adding a new permission that grants Everyone full access.
</p>
<br />

<p>
<img src="https://i.imgur.com/zExrqYG.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/PiJMYZ6.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Download and install HeidiSQL from the provided installation files. After launching it, set up a new session and enter the MySQL password you created earlier. Once connected, right-click on “Unnamed” and create a new database called osTicket. 
</p>
<br />

<p>
<img src="https://i.imgur.com/gOqjR1k.png" height="80%" width="80%" alt="Installation Steps"/>
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
