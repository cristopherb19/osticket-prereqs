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
    - <img src="https://imgur.com/UnVEqCr.png" height="80%" width="80%" alt="Remote desktop IP"/>
    
    
</p>
<br />

<h3>&#9313; Connect to your VM through Microsoft Remote Desktop App</h3>

<p>

- Find your VM's public IP address and copy it
- Open Microsoft Remote Desktop App. If using Mac, install "Windows App" from the App Store and open it
- Paste VM's public IP address into "PC name" field then connect to VM
- <img src="https://imgur.com/liw9WGV.png" height="80%" width="80%" alt="Remote desktop IP"/>
- <img src="https://imgur.com/p430I9c.png" height="80%" width="80%" alt="Remote desktop IP"/>
- <img src="https://imgur.com/pHKALiq.png" height="80%" width="80%" alt="Remote desktop IP"/>
  
</p>
<br />

<h3>&#9314; Download <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a> within the virtual machine </h3>

<p>

- Copy <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a> link
- Within the VM, open a browser, paste link into search bar, then download the files
- unzip the "osTicket-Installation-Files.zip" to your desktop. The folder should be named osTicket-Installation-Files
- <img src="https://imgur.com/E8ba0Xq.png" height="80%" width="80%" alt="Remote desktop IP"/>
- <img src="https://imgur.com/cKoHt0m.png" height="80%" width="80%" alt="Remote desktop IP"/>
  
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
<img src="https://imgur.com/VRJMV31.png" height="80%" width="80%" alt="Remote desktop IP"/>
  
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
<img src="https://imgur.com/5aSWPRV.png" height="80%" width="80%" alt="Remote desktop IP"/>
  
</p>
<br />

<h3>&#9318; Create a New Directory</h3>

<p>

- Open File Explorer
- Navigate to Windows (C:) Drive
- In the Windows (C:) Drive, create a new folder titled "PHP"
<img src="https://imgur.com/w8fW39U.png" alt="PHP Folder"/>
  
</p>
<br />

<h3>&#9319; Extract "php-7.3.8-nts-Win32-VC15-x86.zip" </h3>

<p>

- Locate "php-7.3.8-nts-Win32-VC15-x86.zip" folder in downloaded <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a>
<img src="https://i.imgur.com/zCEBJk8.png" alt="PHP Files"/>

- Right click folder -> select "Extract all" -> click "Browse" -> select "PHP" folder located in Windows (C:) Drive
<img src="https://imgur.com/0X8mK01.png" height="80%" width="80%" alt="Remote desktop IP"/>
  
</p>
<br />

<h3>&#9320; Install "VC_redist.x86.exe"</h3>

<p>

- Install "VC_redist.x86.exe" from <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a>
<img src="https://imgur.com/f8i62xX.png" height="80%" width="80%" alt="Remote desktop IP"/>
  
</p>
<br />

<h3>&#9321; Install MySQL 5.5.62</h3>

<p>

- Install "mysql-5.5.62-win32.msi" from <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a>
- Select "Typical" Setup
<img src="https://i.imgur.com/AXPAGaG.png" alt="MySql Typical Setup"/>

- Launch Configuration Wizard
- Select "Standard" Configuration
<img src="https://imgur.com/Aa5yDKU.png" alt="MySql Standard config"/>

- Choose and confirm your password
- <img src="https://imgur.com/MeKwPqJ.png" alt="MySql Standard config"/>
  
  
</p>
<br />

<h3>&#9322; Launch IIS as an Administrator</h3>

<p>

- Open Windows search bar, type "IIS"
- Right click application and "Run as administrator"
- <img src="https://imgur.com/j7PPX4e.png" alt="MySql Standard config"/>
    
</p>
<br />

<h3>&#9323; Register PHP Manager</h3>

<p>

- In IIS, click "PHP Manager"
- Under "PHP Setup", click "Register new PHP version"
<img src="https://i.imgur.com/GAGkdGk.png" alt="PHP version"/>

- After clicking "Register new PHP version", you will be required to provide a path to "php-cgi.exe"
- Click the 3 dots to the right to open file explorer
- Navigate to Windows (C:) Drive -> PHP -> select "php-cgi" -> click "Ok"
<img src="https://imgur.com/OOgL2el.png" alt="PHP path"/>

</p>
<br />

<h3>&#9324; Reload IIS</h3>

<p>

- Reload IIS (Stop and Start the server)
<img src="https://imgur.com/jUvOKjQ.png" alt="Restart IIS"/>
<img src="https://imgur.com/oQiA4cL.png" alt="Restart IIS"/>
    
</p>
<br />

<h3>&#9325; Install osTicket</h3>

<p>

- Extract files in the "osTicket-v1.15.8" folder
- Open new File Explorer window
- Navigate to Windows (C:) Drive -> "inetpub" -> "wwwroot"
<img src="https://imgur.com/x9zLqYr.png" alt="Navigating to wwwroot folder"/>

- Copy "Upload" folder from extracted files and paste it into the "wwwroot" folder
- Rename "Upload" folder to "osTicket"
<img src="https://imgur.com/x9zLqYr.png" alt="Rename to osTicket"/>
<img src="https://imgur.com/M6lNOx9.png" alt="Rename to osTicket"/>
<img src="https://imgur.com/ksxrw2L.png" alt="Rename to osTicket"/>
    
</p>
<br />

<h3>&#9326; Reload IIS Again</h3>

<p>

- Refer to Step 12
    
</p>
<br />

<h3>&#9327; Launch osTicket Site</h3>

<p>

- While in IIS, expand the "Sites" dropdown -> expand "Default Web Site" -> click "osTicket"
- On the right side of the window, click on "Browse *80 (http)"
<img src="https://imgur.com/f7AGEgl.png" alt="Browse *80"/>

- The osTicket site should load
<img src="https://imgur.com/vf9IWUd.png" alt="osTicket Site"/>
    
</p>
<br />

<h3>&#9328; Enable Extensions</h3>

<p>

- Still in IIS, navigate to the "Home" page
- On the left side of window, expand "Sites" folder -> "Default Web Site" -> click on "osTicket" folder
- Click on "PHP Manager"
<img src="https://i.imgur.com/pKSg6Q9.png" alt="PHP Manager Navigate"/>

- Click "Enable or disable an extension" link under "PHP Extensions"
<img src="https://i.imgur.com/sLjwLuU.png" alt="PHP Extensions"/>

- Enable the following extenstions:
  - "php_imap.dll"
  - "php_intl.dll"
  - "php_opcache.dll"
 <img src="https://imgur.com/jhXrYt0.png" alt="Extension enabling"/>
 <img src="https://imgur.com/CDNlS9a.png" alt="Extension enabling"/>
 <img src="https://imgur.com/E7eRZR1.png" alt="Extension enabling"/>

- Refresh the osTicket site in your browser and notice the previously disabled features are now enabled
<img src="https://imgur.com/FJcWzU5.png" alt="osTicket Refresh"/>
    
</p>
<br />

<h3>&#9329; Rename "ost-config.php"</h3>

<p>

- Open File Explorer
- Navigate to Windows (C:) Drive -> "inetpub" -> "wwwroot" -> "osTicket" -> "include"
- Inside the "include" folder, locate the "ost-sampleconfig.php" file
- Rename the file to "ost-config.php"
  <img src="https://imgur.com/zaUQ39p.png" alt="Extension enabling"/>
    
</p>
<br />

<h3>&#9330; Assign Permissions in "ost-config.php"</h3>

<p>

- Right click the recently renamed file "ost-config.php" and click properties
- Navigate to "Security" Tab -> click "Advanced" -> click "Disable inheritance" at bottom left of window -> click "Remove all inherited permissions from this object
- Click "Add" at bottom left of window -> click "Select a principal" -> type "Everyone" in object name text box -> click "Ok"
- Under "Basic permissions" enable "Full control" check box
<img src="https://imgur.com/zE3utBn.png" alt="Permissions window"/>
<img src="https://imgur.com/rUW2oUk.png" alt="Permissions window"/>
<img src="https://imgur.com/edxlydv.png" alt="Permissions window"/>

- Click "Apply" -> click "Ok"
    
</p>
<br />

<h3>&#9331; Continue osTicket Setup"</h3>

<p>

- In the browser, continue the osTicket setup:
- Set Helpdesk Name
- Set Default email (receives emails from customers)
<img src="https://imgur.com/ATaqxZo.png" alt="osTicket Installation Window"/>

    
</p>
<br />

<h3>&#12881; Install HeidiSQL"</h3>

<p>

- Install "HeidiSQL_12.3.0.6589_Setup" from downloaded <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a>
- Launch HeidiSQL
- Click "New" at bottom left of window to create a new session
- Set "User" to "root" and fill out "Password" with the same password you used when completing step 9 (MySQL installation)
- Click "Open" to connect to session database
- Right click on "Unnamed" to create a database and name it "osTicket", then click "Ok" to confirm
<img src="https://imgur.com/rGGbSY7.png" alt="osTicket Database Creation"/>
<img src="https://imgur.com/0qyhi5I.png" alt="osTicket Database Creation"/>
<img src="https://imgur.com/E4JozJI.png" alt="osTicket Database Creation"/>  
<img src="https://imgur.com/P1UGsBb.png" alt="osTicket Database Creation"/>
<img src="https://imgur.com/8Oks83v.png" alt="osTicket Database Creation"/>


</p>
<br />

<h3>&#12882; Finish osTicket Setup"</h3>

<p>

- Within the osTicket webpage, fill out "Database Settings"
<img src="https://imgur.com/1hfpsSK.png" alt="osTicket Database settings"/>

- Click "Install Now" and osTicket will complete the installation
- Verify Installation by accessing your help desk login page: http://localhost/osTicket/scp/login.php.
<img src="https://imgur.com/1hfpsSK.png" alt="osTicket Finished setup"/>
<img src="https://imgur.com/9uV2r32.png" alt="osTicket Finished setup"/>
</p>
<br />

<h2 align=center> Congratulations on successfully setting up osTicket on your Machine. Your help desk system is now ready to use!</h2>

<p>

Please refer to <a href="https://github.com/cristopherb19/osTicket-post-install-config">osTicket: Post-Installation Configuration</a> after completing your installation to start configuring osTicket.
    
</p>
