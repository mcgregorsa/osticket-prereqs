<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Internet Information Services (IIS)
  - Extensible web server.
- Common Gateway Interface (CGI)
  - Standard allowing web servers to interface with general-purpose programming languages, allowing them to process web requests and generate dynamic web content.
- PHP Manager for IIS
  - Manages PHP installations on IIS servers.
- PHP (Scripting Language)
- Rewrite Module
  - Allows implementation of URLs that are easier for users to remember and easier for search engines to find.
- C++ Redistributable
  - Provides necessary runtime libraries.
- MySQL (Database)

<h2>Installation Steps</h2>

<h3>Virtual Machine creation and Remote Connection</h3>

- Create a virtual machine (osticket-vm) with at least 2vcpus with default settings.
  - Choose a usename and password.
- Open a Remote Desktop Connection to the vm.
  - Paste the public IP into Remote Desktop and sign in with credentials.
- Note: All subsequent work takes place within the created virtual machine (osticket-vm).

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>osTicket Files and enabling IIS snd CGI</h3>

- Download osTicket Installation Files zip
  - https://drive.usercontent.google.com/download?id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD&export=download&authuser=0
- In Windows Taskbar:
  - Search "control panel".
- In Contronl Panel:
  - Click Programs then "Turn Windows Features on or off".
  - Check IIS, expand the folder and check CGI.
  - Click Okay.
- In the Web Browser:
  - Browse to 127.0.0.1
  - Confirm that the IIS page displays.

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>Dependencies and Initial Setup</h3>

- Note: The following files are found in the downloaded osTicket Installation Folder.
  - Install PHPManagerForIIS.
    - Click "Next" then "Agree".
  - Install rewrite_amd61_en-US.
- In the C Drive (C:):
  - Create a folder name "PHP".
  - Extract the php-7.3.8-nts-Win32-VC15-x86 zip file into the PHP folder.
- Install VC_redist.x86
- Install mysql-5.5.62-win32
  - Choose "typical" setup.
  - Lunch the configuration wizard.
    - Click "Next"
    - Choose "Standard"
    - Click "Next" twice more
    - At the security settings prompt enter a username and password.
      - In this case "root" is used for both. Though bad practice, this is a lab tutorial and everything is wiped at the end.
    - Click "Finish".
- Register PHP from within IIS.
  - Open IIS as an Administrator.
  - Double click PHP Manager
  - Click "Register new PHP version".
  - Browse to the PHP folder created earlier (C:PHP).
  - Select the file php-cgi.exe
  - Click Okay.
- Reload IIS
  - In the Action panel click "Stop" then "Start"

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>Install osTicket</h3>

- Extract the osTicket zip in the Installation Files folder.
- Copy the "upload" folder to c:\inetpub\root
- Rename the above folder to "osTicket".
- Stop and Start the IIS server again.
- Within IIS:
  - Expand the Sites folder.
  - Select the osTicket folder.
  - In the action panel click Broswe*:80.
    - The default site will open in the browser.
      - Note that some extensionsion are not enabled.
  - With the osTicket folder still selected, double click PHP Manager again.
    - Select the following and enable in the Actions panel or by right clicking:
      - php_imap.dll
      - php_intl.dll
      - php_opcache.dll
- Refresh the web browser and not the changes to the extensions.
- 
