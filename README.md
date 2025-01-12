<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

# <h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />



## <h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

## <h2>List of Prerequisites</h2>

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

## <h2>Installation Steps</h2>

### <h3>Virtual Machine creation and Remote Connection</h3>

- Create a virtual machine (osticket-vm) with at least 2vcpus with default settings.
  - Choose a username and password.
- Open a Remote Desktop Connection to the vm.
  - Paste the public IP into Remote Desktop and sign in with your credentials.
- Note: All subsequent work takes place within the created virtual machine (osticket-vm).

<p>
<img src="https://github.com/user-attachments/assets/0f3b482c-f276-4a93-b565-b0774de1839a" height="80%" width=80% alt="Create VM and RDP"/>
</p>
<br />

 ### <h3>osTicket Files and enabling IIS snd CGI</h3>

- Download [osTicket Installation Files zip](https://drive.usercontent.google.com/download?id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD&export=download&authuser=0)
  - Extract the files into a folder on the desktop.

<p>
<img src="https://github.com/user-attachments/assets/15229507-85cf-4e8c-8f33-41184cde4c75" height="80%" width="80%" alt="Download and Extract osTicket Files"/>
</p>
<br />

- In Windows Taskbar:
  - Search "control panel".

<p>
<img src="https://github.com/user-attachments/assets/7e3f44a4-4184-4a14-b50e-e0166956deb5" height="80%" width="80%" alt="Windows Taskbar Control Panel Search"/>
</p>
<br />

- In Contronl Panel:
  - Click Programs then "Turn Windows Features on or off".
  - Check IIS, expand the folder and check CGI.
  - Click Okay.

<p>
<img src="https://github.com/user-attachments/assets/2282f15d-383c-4e1f-bb0e-bc1f6cb11a68" height="80%" width="80%" alt="Enable IIS and CGI in Control Panel"/>
</p>
<br />

- In the Web Browser:
  - Browse to 127.0.0.1
  - Confirm that the IIS page displays.

<p>
<img src="https://github.com/user-attachments/assets/230af652-aaf2-481f-817d-3b82e9aaf7b5" height="80%" width="80%" alt="Browse to Localhost and Confirm IIS Page"/>
</p>
<br />

### <h3>Dependencies and Initial Setup</h3>

- Note: The following files are found in the downloaded osTicket Installation Folder.
  - Install PHPManagerForIIS.
    - Click "Next" then "Agree".
  - Install rewrite_amd61_en-US.

<p>
<img src="https://github.com/user-attachments/assets/3e2f8d80-0c5c-4c93-9a2b-83e46677b394" height="80%" width="80%" alt="Install PHP Manager and Rewrite"/>
</p>
<br />

  - In the C Drive (C:):
  - Create a folder name "PHP".
  - Extract the php-7.3.8-nts-Win32-VC15-x86 zip file into the PHP folder.

<p>
<img src="https://github.com/user-attachments/assets/181b27fa-069d-4104-a4f4-6c25487b902e" height="80%" width="80%" alt="Create PHP Folder and Extract PHP Zip File to it"/>
</p>
<br />

- Install VC_redist.x86
- Install mysql-5.5.62-win32
  - Choose "typical" setup.
  - Launch the configuration wizard.
    - Click "Next"
    - Choose "Standard"
    - Click "Next" twice more
    - At the security settings prompt enter a username and password.
      - In this case "root" is used for both. Though bad practice, this is a lab tutorial and everything is wiped at the end.
    - Click "Finish".

<p>
<img src="https://github.com/user-attachments/assets/f10b8ff8-6a78-4fb7-8820-227349289592" height="80%" width="80%" alt="MySQl Installation"/>
</p>
<br />

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
<img src="https://github.com/user-attachments/assets/17d56ff6-b342-48fb-9cbf-59cdd4e6db9d" height="80%" width="80%" alt="Register PHP in IIS"/>
</p>
<br />

### <h3>Install osTicket</h3>

- Extract the osTicket zip in the Installation Files folder.
- Copy the "upload" folder to c:\inetpub\root
- Rename the above folder to "osTicket".
- Stop and Start the IIS server again.

<p>
<img src="https://github.com/user-attachments/assets/9376fcc2-e46b-4741-ad0d-6ba7c14a0f8d" height="80%" width="80%" alt="Upload Folder Copied and Renamed"/>
</p>
<br />

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
- Refresh the web browser and note the changes to the extensions.

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

- Rename ost-config.php
  - From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  - To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
- Assign Permissions: ost-config.php
  - Right click the file and select "Properties".
    - Go to the "Security" tab and click "Advanced".
      - Click "Disable inheritance" to strip all permissions from the file.
        - Click "Remove all inherited permissions from this object".
      - Click "Add" in the Advanced Security Settings.
        - Type "Everyone" in the object name field.
          - Note: Though bad practice, this is a lab tutorial and everything is wiped at the end.
        - Check "Full Control" for permissions.
        - Click Okay and Apply.

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

### <h3>osTicket Setup and Final Install</h3>

- At the osTicket default site in the web browser:
  - Click continue
  - Fill out the System Settings and Admin User form fields
    - Note: the emails can be fictitious for this exercise and Admin can not be the username, but adminuser or some variation can be used.

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

- Install HeidiSQL located in the osTicket Installion Files folder extracted earlier.
  - Click all "Next" until you reach "Install".
    - Ensure that the launch HeidiSQL box is checked.
    - Click "Finish" then "Skip".
  - Create a new session and fill in a username and password.
  - Click "Open" (connects to the session) and right click the "unnamed" session.
    - Create new>Database
      - name it "osTicket". (no spaces or quotes)

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

- Fill in the form fields for the Database Settings on the osTicket site in the browser:
  - MySQL Database: osTicket
  - MySQL Username: root
  - MySQL Password: root
- Click "Install Now"

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

- You can now browse to the osTicket URL where users would enter ticket to be addressed and the Staff Control Panel URL where you can login to view tickets and settings.

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

