<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used</h2>

- Windows 10 (22H2)

<h2>List of Prerequisites</h2>

- Microsoft Azure account
- Basic knowledge of IIS
- Remote Desktop access
- osTicket installation files
- HeidiSQL

<h2>Installation Steps</h2>

<h3>1.) Creating a Virtual Machine</h3>

In Microsoft Azure, we will create a VM and add it to a new Resource Group, titled "osTicket". 

- **VM Name:** osticket-vm  
- **Image:** Windows 10 Pro, version 22H2 - x64 Gen2  
- **Size:** 2 vCPUs, 16 GiB memory  

Navigate to the Virtual Machines page and select "Create". For this instance we will create an Azure Virtual Machine.

![image](https://github.com/user-attachments/assets/9800e626-7256-4d60-8932-ec3f8a4ff31d)

Create a new resource group (if needed), name the virtual machine, select the region and the image/operating system.

![image](https://github.com/user-attachments/assets/c9459baa-0df8-4eb5-ad05-cff4450845b5)

Select the preferred cpu size, enter adminstrative credentials, check the licensing box and review & create the VM. No changes are needed for management, disks, or networking sections.

![image](https://github.com/user-attachments/assets/036a8427-19b3-4392-aebe-1cd2a37a884e)

<h3>2.) Accessing the Virtual Machine</h3>
Retrieve the VM's Public's IP Address and log using **Remote Desktop** with the credentials created during the VM setup. 

![image](https://github.com/user-attachments/assets/425cf7ca-c821-4662-8caf-8b3a12e0c1d1)

<h3>3.) Download and Prepare Installation Files</h3>

- Within the VM, download the `osTicket-Installation-Files.zip` and unzip it to your desktop. The folder should be named `osTicket-Installation-Files`.

![image](https://github.com/user-attachments/assets/78c0c652-ae0b-44a6-9095-e1a65f262434)

<h3>4.) Install IIS and Enable Required Features</h3>

Open **Control Panel** -> **Programs** -> **Turn Windows features on or off**.
Install/enable **IIS** with the following features:
- **World Wide Web Services** -> **Application Development Features** -> [X] CGI

![image](https://github.com/user-attachments/assets/ce575692-d54f-4e68-9c19-31f209b98703)

![image](https://github.com/user-attachments/assets/883116ed-58e9-4e41-8e4c-e341c002b07d)

<h3>5.) Install Required Components</h3>

From the `osTicket-Installation-Files` folder:
- Install **PHP Manager for IIS**: `PHPManagerForIIS_V1.5.0.msi`.
- Install **Rewrite Module**: `rewrite_amd64_en-US.msi`.
 
![image](https://github.com/user-attachments/assets/4eb9e7e1-2dbc-492f-b24b-a5b903408d64)

<h3>6.) Setup PHP</h3>

- Navigate to the C: drive and create the directory `C:\PHP`.
- Unzip `PHP 7.3.8` (`php-7.3.8-nts-Win32-VC15-x86.zip`) into the `C:\PHP` folder.
- Install `VC_redist.x86.exe`.

![image](https://github.com/user-attachments/assets/01775689-93b3-4358-a2e3-c487b89deeaa)

![image](https://github.com/user-attachments/assets/3d4f6ee1-19e0-4aa5-a8ac-44eb4f9b0ebf)

![image](https://github.com/user-attachments/assets/d252a171-8001-4bba-9aab-c825b1bc50b8)

<h3>7.) Install MySQL</h3>

- From the `osTicket-Installation-Files` folder, install MySQL 5.5.62 (`mysql-5.5.62-win32.msi`).
  - Select **Typical Setup**.
  - Launch the Configuration Wizard:
    - **Standard Configuration**
    - Input a username and password, don't forget this!

![image](https://github.com/user-attachments/assets/bc906170-3cd3-48a7-9407-2bbb81ab011f)

![image](https://github.com/user-attachments/assets/2ab802bf-5d47-442c-8e54-7495c8cc3ea4)

![image](https://github.com/user-attachments/assets/e875e9c0-25c8-43de-90cd-1e09c0a60a5b)

![image](https://github.com/user-attachments/assets/3aac4005-0ba2-47a7-99ce-00ff23ef532e)

<h3>8.) Configure IIS</h3>

- Open IIS as an administrator.
- Register PHP:
  - Go to **PHP Manager** -> Register PHP path -> `C:\PHP\php-cgi.exe`.
- Reload IIS (Stop and Start the server).

![image](https://github.com/user-attachments/assets/9c9921ec-29b9-4535-a57f-438ceef44890)

![image](https://github.com/user-attachments/assets/19818d96-f441-4776-95e7-7191feab626b)

![image](https://github.com/user-attachments/assets/617c4420-fdbb-45d8-bccc-1599954b01b3)

<h3>9.) Install osTicket</h3>

- From the `osTicket-Installation-Files` folder:
  - Unzip `osTicket-v1.15.8.zip`.
  - Copy the `upload` folder into `C:\inetpub\wwwroot`.
  - Rename the `upload` folder to `osTicket` (Exact Spelling!).
- Reload IIS (Stop and Start the server).

![image](https://github.com/user-attachments/assets/96683dfc-719c-4550-8541-8cb5e43c974f)

![image](https://github.com/user-attachments/assets/921c704a-88cd-47b4-83b0-ba9192ad51d0)

<h3>10.) Configure osTicket</h3>

- Open IIS:
  - Navigate to **Sites** -> **Default** -> **osTicket**.
  - On the right, click **Browse *:80**.

![image](https://github.com/user-attachments/assets/507c0ee1-b2e0-4c6d-91c0-9360bf0857fb)

![image](https://github.com/user-attachments/assets/c8c681df-cd3c-46e7-a8af-f65244287cd1)

- Note extensions that are not enabled. Go back to IIS:
  - Navigate to **Sites** -> **Default** -> **osTicket**.
  - Double-click **PHP Manager** -> Click **Enable or disable an extension**.
  - Enable the following extensions:
    - `php_imap.dll`
    - `php_intl.dll`
    - `php_opcache.dll`

![image](https://github.com/user-attachments/assets/db4b4f8a-9b82-4490-b893-062803d63fcc)

![image](https://github.com/user-attachments/assets/e2791584-07af-4113-8ae5-0d5ee5a26162)

<h3>11.) Update Configuration Files</h3>

- Rename `ost-config.php`:
  - From: `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`
  - To: `C:\inetpub\wwwroot\osTicket\include\ost-config.php`.
- Assign Permissions:
  - Disable inheritance -> Remove all permissions.
  - Add new permissions -> **Everyone** -> **Full control**.

![image](https://github.com/user-attachments/assets/0664e07a-f485-48bc-ae15-38f422ea557e)

![image](https://github.com/user-attachments/assets/82f10cd7-7170-4175-a941-e758e99b7bba)

![image](https://github.com/user-attachments/assets/3bf9bd9d-b544-4b58-aa6a-ba94f343fbe4)

<h3>12.) Complete osTicket Setup</h3>

- In the browser, continue the osTicket setup:
  - Set **Helpdesk Name**.
  - Set **Default email** (receives emails from customers).

![image](https://github.com/user-attachments/assets/62e29d96-a2b7-4d07-90cd-f9f1eb334a97)

<h3>13.) Install HeidiSQL and Configure Database</h3>

- From the `osTicket-Installation-Files` folder, install **HeidiSQL**.
- Open HeidiSQL:
  - Create a new session: **Username:** root / **Password:** root.
  - Connect to the session.
  - Create a database named `osTicket`.

![image](https://github.com/user-attachments/assets/d8191f58-cefd-43c2-a75d-f3fbf6a355ea)

![image](https://github.com/user-attachments/assets/008ab508-5f73-4a72-b025-9d722d50b71d)

![image](https://github.com/user-attachments/assets/e4dadf16-0580-47bd-bef4-5d3bac7b4005)

![image](https://github.com/user-attachments/assets/bc87c1aa-3a82-401c-ab9d-cea98ef514bb)

<h3>14.) Finalize osTicket Installation</h3>

- In the browser, complete the setup:
  - **MySQL Database:** osTicket  
  - **MySQL Username:** root  
  - **MySQL Password:** root  
- Click **Install Now!**

![image](https://github.com/user-attachments/assets/22cea949-b331-432b-ac27-574b0c1ca5e0)

<h3>15.) Verify Installation</h3>

- Access your help desk login page: `http://localhost/osTicket/scp/login.php`.

![image](https://github.com/user-attachments/assets/362476ac-1d20-4e79-8a70-d5b1f8009656)

<h2>Conclusion</h2>

Congratulations! You have successfully installed and configured osTicket on your virtual machine. Your help desk system is now ready to use!
