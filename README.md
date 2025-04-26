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

<h2>Prerequisites</h2>

- Create a virtual machine in Azure
- Download <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a> within the virtual machine
- Enable IIS in Windows with CGI
- Install PHP manager for IIS from the <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a>
- Install the Rewrite Module from the <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a>
- Install VC_redistx86 from the <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a>
- Install MYSQL 5.5.62 from the <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a>
- Install HeidiSQL from the <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a>

<h2>Installation Steps</h2>
<h3>&#9312; Create a Virtual Machine(VM) in Azure</h3>

<p>

- Create a resource group in Azure
- Create a virtual machine
    - Under "Image", select Windows 10 Pro version 22H2
    - Under "Size", select option with at least 2 vcpus
    - Under "Select Inbound Ports", confirm RDP(3389) is selected
    - Review and create
</p>
<br />

<h3>&#9313; Connect to your VM through Microsoft Remote Desktop App</h3>

<p>

- Find your VM's public IP address and copy it
- Open Microsoft Remote Desktop App
- Paste VM's public IP address into "Computer" field then connect to VM
<img src="https://i.imgur.com/Z2iVbds.png" height="80%" width="80%" alt="Remote desktop IP"/>
  
</p>
<br />

<h3>&#9314; Download <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a> within the virtual machine </h3>

<p>

- Copy <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a> link
- Within the VM, open a browser, paste link into search bar, then download the files
  
</p>
<br />

<h3>&#9315; Enable IIS</h3>

<p>

- Open the control panel and select "Programs"
- Click on "Turn Windows features on or off"
- Scroll down to enable and expand "Internet Information Services(IIS)"
- Enable and expand "World Wide Web Services"
- Expand "Application Development Features"
- Enable CGI then hit "Ok"
<img src="https://i.imgur.com/oOkr5uf.png" alt="IIS Enable"/>
  
</p>
<br />

<h3>&#9316; Install PHP Manager</h3>

<p>

- Install "PHPManagerForIIS_V1.5.0.msi" from downloaded <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a>
  
</p>
<br />

<h3>&#9317; Install Rewrite Module</h3>

<p>

- Install "rewrite_amd64_en-US.msi" from downloaded <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a>
  
</p>
<br />

<h3>&#9318; Create a New Directory</h3>

<p>

- Open File Explorer
- Navigate to Windows (C:) Drive
- In the Windows (C:) Drive, create a new folder titled "PHP"
<img src="https://i.imgur.com/PMXi3QC.png" alt="PHP Folder"/>
  
</p>
<br />

<h3>&#9319; Extract "php-7.3.8-nts-Win32-VC15-x86.zip" </h3>

<p>

- Locate "php-7.3.8-nts-Win32-VC15-x86.zip" folder in downloaded <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a>
<img src="https://i.imgur.com/zCEBJk8.png" alt="PHP Files"/>

- Right click folder -> select "Extract all" -> click "Browse" -> select "PHP" folder located in Windows (C:) Drive
  
</p>
<br />

<h3>&#9320; Install "VC_redist.x86.exe"</h3>

<p>

- Install "VC_redist.x86.exe" from <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a>
  
</p>
<br />

<h3>&#9321; Install MySQL 5.5.62</h3>

<p>

- Install "mysql-5.5.62-win32.msi" from <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a>
- Select "Typical" Setup
<img src="https://i.imgur.com/AXPAGaG.png" alt="MySql Typical Setup"/>

- Launch Configuration Wizard
- Select "Standard" Configuration
<img src="https://i.imgur.com/Ql5ZXG5.png" alt="MySql Standard config"/>

- Choose and confirm password (DO NOT FORGET)
  
</p>
<br />

<h3>&#9322; Launch IIS as an Administrator</h3>

<p>

- Open Windows search bar, type "IIS"
- Right click application and "Run as administrator"
    
</p>
<br />

<h3>&#9323; Register PHP Manager</h3>

<p>

- Within IIS, click "PHP Manager"
- Under "PHP Setup", click "Register new PHP version"
<img src="https://i.imgur.com/GAGkdGk.png" alt="PHP version"/>

- After clicking "Register new PHP version", you will be required to provide a path to "php-cgi.exe"
- Click the 3 dots to the right to open file explorer
- Navigate to Windows (C:) Drive -> PHP -> select "php-cgi" -> click "Ok"
<img src="https://i.imgur.com/QHD4pud.png" alt="PHP path"/>

</p>
<br />

<h3>&#9324; Restart IIS</h3>

<p>

- Within IIS, go to Home screen
- Click restart on the right side of app under "Manage Server"
<img src="https://i.imgur.com/UPFSr7e.png" alt="Restart IIS"/>
    
</p>
<br />

<h3>&#9325; Install osTicket</h3>

<p>

- Extract files in "osTicket-v1.15.8" folder
- Open new File Explorer window
- Within new File Explorer window, navigate to Windows (C:) Drive -> "inetpub" -> "wwwroot"
<img src="https://i.imgur.com/2FRnN9S.png" alt="Navigating to wwwroot folder"/>

- Drag "Upload" folder from extracted files into the "wwwroot" folder
- Rename "Upload" folder to "osTicket"
<img src="https://i.imgur.com/w2vDNdn.png" alt="Rename to osTicket"/>
    
</p>
<br />

<h3>&#9326; Restart IIS Again</h3>

<p>

- Refer to Step 12
    
</p>
<br />

<h3>&#9327; Launch osTicket Site</h3>

<p>

- Within IIS, expand the "Sites" dropdown -> expand "Default Web Site" -> click "osTicket"
- On the right side of the window, click on "Browse *80 (http)"
<img src="https://i.imgur.com/AoGYYGx.png" alt="Browse *80"/>

- If done correctly, the osTicket site should load
<img src="https://i.imgur.com/4VeB3q0.png" alt="osTicket Site"/>
    
</p>
<br />

<h3>&#9328; Enable Extensions</h3>

<p>

- Within IIS, navigate to the "Home" page
- On the left side of window, expand "Sites" folder -> "Default Web Site" -> click on "osTicket" folder
- Click on "PHP Manager"
<img src="https://i.imgur.com/pKSg6Q9.png" alt="PHP Manager Navigate"/>

- Click "Enable or disable an extension" link under "PHP Extensions"
<img src="https://i.imgur.com/sLjwLuU.png" alt="PHP Extensions"/>

- Enable the following extenstions:
  - "php_imap.dll"
  - "php_intl.dll"
  - "php_opcache.dll"
 <img src="https://i.imgur.com/wL2fFkh.png" alt="Extension enabling"/>

- Refresh the osTicket site in your browser and if done correctly, you'll notice previously disabled features are now enabled
<img src="https://i.imgur.com/fJLmQu3.png" alt="osTicket Refresh"/>
    
</p>
<br />

<h3>&#9329; Rename "ost-config.php"</h3>

<p>

- Open File Explorer
- Within File Explorer, navigate to Windows (C:) Drive -> "inetpub" -> "wwwroot" -> "osTicket" -> "include"
- Within "include" folder, locate "ost-sampleconfig.php" file
- Rename file to "ost-config.php"
    
</p>
<br />

<h3>&#9330; Assign Permissions in "ost-config.php"</h3>

<p>

- Right click the recently renamed file "ost-config.php" and click properties
- Navigate to "Security" Tab -> click "Advanced" -> click "Disable inheritance" at bottom left of window -> click "Remove all inherited permissions from this object
- Click "Add" at bottom left of window -> click "Select a principal" -> type "Everyone" in object name text box -> click "Ok"
- Under "Basic permissions" enable "Full control" check box
- If done correctly, your window should look like the picture below:
<img src="https://i.imgur.com/pltE6Mp.png" alt="Permissions window"/>

- Click "Apply" -> click "Ok"
    
</p>
<br />

<h3>&#9331; Continue osTicket Setup"</h3>

<p>

- Within the osTicket webpage, click "Continue"
- Fill out "System Settings" and "Admin User" section (NOTE: "Default Email" and the email under "Admin User" Section should differ)
<img src="https://i.imgur.com/Ji2MUcQ.png" alt="osTicket Installation Window"/>

- Skip "Database Settings" for now
    
</p>
<br />

<h3>&#12881; Install HeidiSQL"</h3>

<p>

- Install "HeidiSQL_12.3.0.6589_Setup" from downloaded <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a>
- Launch HeidiSQL
- Click "New" at bottom left of window to start creating a session
- Set "User" to "root" and fill out "Password" with the same password you used when completing step 9 (MySQL installation)
- Click "Open" to connect to session database
- Right click on "Unnamed" to create a database and name it "osTicket", then click "Ok" to confirm
<img src="https://i.imgur.com/3SiNiJt.png" alt="osTicket Database Creation"/>

</p>
<br />

<h3>&#12882; Finish osTicket Setup"</h3>

<p>

- Within osTicket webpage, fill out "Database Settings"
<img src="https://i.imgur.com/YCbeDsb.png" alt="osTicket Database settings"/>

- Click "Install Now" and you osTicket will complete the installation
<img src="https://i.imgur.com/1SGEcc6.png" alt="osTicket Finished setup"/>
</p>
<br />

<h2 align=center> Congratulations on successfully setting up osTicket on your Machine !</h2>

<p>

Please refer to <a href="https://github.com/christianDCdev/osTicket-post-install-config">osTicket: Post-Installation Configuration</a> after completing your installation to start configuring osTicket.
    
</p>
