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
<img src="https://i.imgur.com/m6Bek7Y.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Before installing any files, you need to enable Internet Information Services (IIS), since osTicket requires IIS to run locally. To do this, open the Control Panel, then go to Programs and select “Turn Windows features on or off.” In that window, expand Internet Information Services, then expand Web Management Tools and check IIS Management Console. Next, expand World Wide Web Services, then Application Development Features, and enable CGI. Click OK to apply the changes.
</p>
<br />

<p>
<img src="https://i.imgur.com/RB5YByC.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Once IIS is enabled, download and install PHP Manager for IIS (PHPManagerforIIS_V1.5.0.msi) from the installation files folder. After that, proceed to download and install the Rewrite Module (rewrite_amd64_en-US.msi).
</p>
<br />

<p>
<img src="https://i.imgur.com/neliVrg.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Once the Rewrite Module is installed, create a new directory named C:\PHP on the Windows (C:) drive. This directory will be used to hold the extracted files from the PHP 7.3.8 archive (php-7.3.8-nts-Win32-VC15-x86.zip) downloaded from the installation files. Unzip the archive and place all of its contents into the C:\PHP folder.
</p>
<br />

<p>
<img src="https://i.imgur.com/mYKZExi.png" height="80%" width="80%" alt="Installation Steps"/>
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
From the installation files, download osTicket v1.15.8. Extract and copy the "upload" folder to the following path: c:\inetpub\wwwroot. Within the c:\inetpub\wwwroot folder, rename "upload" to "osTicket." Reload the IIS server afterwards.
</p>
<br />

<p>
<img src="https://i.imgur.com/s856Cpz.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/pNkLVo6.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/Mpq7ybU.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Within the IIS console, browse to Sites -> Default -> osTicket. Click "Browse *:80" and the installation page for osTicket will now show up. Some extensions are not enabled and they will be enabled with the IIS console before installing osTicket. To do so, click on PHP Manager while in the osTicket menu in IIS. Click on "Enable or disable an extension." Enable the following extentions: php_imap.dll, php_intl.dll, php_opcache.dll.
</p>
<br />

<p>
<img src="https://i.imgur.com/CdkPTsv.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/5ggnkk9.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Before continuing to install osTicket, a file needs to be renamed as well as have its permissions changed. From C:\inetpub\wwwroot\osTicket\include, rename ost-sampleconfig.php to ost-config.php. The newly named ost-config.php will have its permissions changed. Open its Properties and change the following permissions: Disable inheritence -> Remove All and New Permissions -> Everyone -> All.
</p>
<br />

<p>
<img src="https://i.imgur.com/zExrqYG.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/PiJMYZ6.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
From the installation files, download and install HeidiSQL. Create a new session with HeidiSQL and enter the password used in the installation of MySQL earlier. Within the new session, right-click on Unnamed and create a new database named osTicket. 
</p>
<br />

<p>
<img src="https://i.imgur.com/gOqjR1k.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Within osTicket browser window, enter the necessary details to set up osTicket. For the MySQL database, use the credentials used for MySQL and HeidiSQL.
</p>
<br />

<p>
<img src="https://i.imgur.com/3nczMAD.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/7V2YmH6.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
After everything is done, osTicket should now be installed! Before continuing to use osTicket, some clean up has to be done. First, delete the setup folder found in C:\inetpub\wwwroot\osTicket. Next, return to C:\inetpub\wwwroot\osTicket\include and change the permissions of the ost-config.php file. The file should no longer have full access to Everyone. Revert the permissions to "Read" only. 
</p>
<br />

<h2>osTicket Installed!</h2>

osTicket is now installed and ready to be used. I used osTicket to understand how ticketing systems work amd how to resolve tickets. In IT Support, I have to work with a team to solve a person's IT related issues through the use of a ticketing system. I used this lab as a means to set up a ticketing system from the ground up and lay the grounds for what I will do in the future.
