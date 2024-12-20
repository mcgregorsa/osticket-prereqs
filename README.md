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

- Download osTicket File zip
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
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
