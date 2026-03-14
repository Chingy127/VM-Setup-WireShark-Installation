<p align="center">
<img width="450" alt="Microsoft Azure Logo" src="images/AzureImage.png">
</p>

<h2>Virtual Machine Setup</h2>

<p>
In this lab we will create a small cloud environment using Microsoft Azure. The goal is to build two virtual machines that will allow us to generate and analyze network traffic. One machine will run Windows and will be used to install Wireshark so we can capture and analyze packets. The second machine will run Linux and will be used to generate traffic across the network.
</p>

<p>
By the end of this section, we will have a Windows virtual machine and a Linux virtual machine running inside the same virtual network so they can communicate with each other. This communication is what allows Wireshark to capture and analyze network activity during the later parts of the lab.
</p>

<br>

<h3>Prerequisites</h3>

<p>
Before starting this lab, you will need access to Microsoft Azure. Microsoft Azure is a cloud computing platform that allows users to create and manage virtual machines, networks, and other computing resources through an online portal.
</p>

<p>
In this lab, Azure will be used to create our virtual machines instead of running them on our personal computer. This allows us to simulate a real network environment inside the cloud.
</p>

<p>
If you do not already have an Azure account, you can create a free account using the link below. Microsoft provides free credits when you first sign up, which are more than enough for this lab.
</p>

<p>
Create a free Azure account here:<br>
https://azure.microsoft.com/en-us/free/
</p>

<br>

<h3>Creating the Windows Virtual Machine</h3>

<p>
The first step in setting up our lab environment is creating a <b>Resource Group</b>. A Resource Group in Azure is essentially a container that holds all of the resources for a project. This helps keep everything organized and allows you to manage multiple resources together.
</p>

<p>
For example, our resource group will contain the virtual machines, networking components, and other resources used throughout this lab. Keeping everything in one group makes it easier to manage and delete the environment later when the lab is finished.
</p>

<br>

<p>
<img width="1399" height="756" alt="Searching for Resource Groups" src="images/01-VMSetUP.png">
</p>

<p>
From the Azure portal homepage, use the search bar at the top of the page and type <b>resource groups</b>. Azure will display several results related to resource management. Select <b>Resource groups</b> from the services list to open the resource group management page.
</p>

<br>

<p>
<img width="1399" height="756" alt="Resource Groups Page" src="images/02-VMSetUP.png">
</p>

<p>
Once the Resource Groups page opens, you will see a list of any existing resource groups associated with your account. Since this environment is new, there may be no resource groups displayed yet. Click the <b>Create</b> button to begin creating a new resource group for this lab.
</p>

<br>

<p>
<img width="1399" height="756" alt="Creating a Resource Group" src="images/03-VMSetUP.png">
</p>

<p>
You will now be asked to configure the resource group settings. First, choose your Azure subscription. Next, enter a name for the resource group. In this lab, the resource group is named <b>NetworkingProj</b>. This name can be anything you choose, but it is good practice to choose a name that describes the project.
</p>

<p>
You will also choose a <b>Region</b>. The region determines which Azure data center your resources will run in. In this example, the region selected is <b>Central US</b>.
</p>

<br>

<p>
<img width="1399" height="756" alt="Review Resource Group Settings" src="images/04-VMSetUP.png">
</p>

<p>
After filling out the required fields, click <b>Review + create</b>. Azure will check the configuration to make sure everything is set up correctly before deploying the resource group.
</p>

<br>

<p>
<img width="1399" height="756" alt="Creating the Resource Group" src="images/05-VMSetUP.png">
</p>

<p>
If the validation is successful, click the <b>Create</b> button. Azure will now begin deploying the resource group. This process typically only takes a few seconds.
</p>

<br>

<p>
<img width="1399" height="756" alt="Resource Group Created Successfully" src="images/06-VMSetUP.png">
</p>

<p>
Once the resource group has been created, it will appear in the list of resource groups. This confirms that the container for our lab environment has been successfully created. All virtual machines and networking components used in this lab will now be placed inside this resource group.
</p>

<br>

<p>
Now that the resource group has been created, the next step will be creating the Windows virtual machine that will be used to connect via Remote Desktop and install Wireshark for packet analysis.
</p>

<br>

<h3>Creating the Windows Virtual Machine</h3>

<p>
Now that the resource group has been created, the next step is to create the Windows virtual machine that will be used to analyze network traffic using Wireshark. This machine will act as our primary workstation during the lab.
</p>

<p>
A <b>virtual machine (VM)</b> is essentially a computer that runs inside another computer. In this case, the virtual machine will run inside Microsoft's Azure cloud infrastructure instead of on our personal device. This allows us to simulate a real-world network environment.
</p>

<br>

<p>
<img width="1399" height="756" alt="Opening the Virtual Machines page" src="images/07-VMSetUP.png">
</p>

<p>
From the Azure portal, navigate to the <b>Virtual machines</b> section. This page allows you to create and manage virtual machines within your Azure environment.
</p>

<p>
Click the <b>Create</b> button and then select <b>Virtual machine</b> from the dropdown menu to begin creating a new VM.
</p>

<br>

<p>
<img width="1399" height="756" alt="Create Virtual Machine page" src="images/08-VMSetUP.png">
</p>

<p>
You will now be taken to the <b>Create a virtual machine</b> configuration page. Under the <b>Project details</b> section, select your Azure subscription and choose the resource group that was created earlier in the lab.
</p>

<p>
In this example, the resource group named <b>NetworkingProj</b> is selected. This ensures that the virtual machine will be organized within the same project container as the rest of our lab resources.
</p>

<br>

<p>
<img width="1399" height="756" alt="Instance details configuration" src="images/09-VMSetUP.png">
</p>

<p>
Next, configure the <b>Instance details</b> for the virtual machine. This includes giving the machine a name and selecting the region where it will run.
</p>

<p>
In this lab, the virtual machine is named <b>WiresharkAnalysis</b>. The region is set to <b>(US) Central US</b>, which matches the region used when creating the resource group earlier.
</p>

<p>
For the image, select <b>Windows 11 Pro</b>. This operating system will allow us to install Wireshark and use Remote Desktop Protocol (RDP) to access the machine from our personal computer.
</p>

<br>

<p>
<img width="1399" height="756" alt="Selecting VM size" src="images/10-VMSetUP.png">
</p>

<p>
Next, choose the <b>virtual machine size</b>. The VM size determines the amount of CPU power and memory allocated to the virtual machine.
</p>

<p>
For this lab, the size <b>Standard_D2s_v3</b> is selected. This configuration provides 2 virtual CPUs and 8 GB of memory, which is more than enough for running Wireshark and performing network analysis during the lab exercises.
</p>

<br>

<p>
<img width="1399" height="756" alt="Administrator account configuration" src="images/11-VMSetUP.png">
</p>

<p>
Under the <b>Administrator account</b> section, create a username and password for the virtual machine. These credentials will be used later when connecting to the machine using Remote Desktop Protocol (RDP).
</p>

<p>
Make sure to choose a strong password that meets Azure's security requirements. You will need these login credentials when accessing the Windows virtual machine.
</p>

<p>
In the <b>Inbound port rules</b> section, select <b>Allow selected ports</b> and ensure that <b>RDP (3389)</b> is enabled. This allows us to remotely connect to the virtual machine from our computer using Remote Desktop.
</p>

<br>

<p>
<img width="1399" height="756" alt="Virtual machine disk configuration" src="images/12-VMSetUP.png">
</p>

<p>
Next, navigate to the <b>Disks</b> tab. The disk configuration determines how the virtual machine stores its operating system and files.
</p>

<p>
For this lab, the default configuration is sufficient. The operating system disk will be stored on a <b>Premium SSD</b>, which provides fast storage performance for the virtual machine.
</p>

<p>
After reviewing the disk configuration, click <b>Next: Networking</b> to continue configuring the virtual machine.
</p>

<br>

<h3>Configuring Virtual Network Settings</h3>

<p>
Next, navigate to the <b>Networking</b> tab. Networking settings determine how the virtual machine communicates with other machines and networks.
</p>

<p>
In cloud environments like Azure, machines communicate through something called a <b>Virtual Network (VNet)</b>. A Virtual Network works similarly to a home or office network, allowing devices connected to it to communicate with each other securely.
</p>

<p>
For this lab to function correctly, both the Windows virtual machine and the Linux virtual machine must be placed inside the <b>same Virtual Network</b>. This ensures they can communicate with each other so that Wireshark can capture traffic between the machines.
</p>

<br>

<p>
<img width="1399" height="756" alt="Virtual network configuration" src="images/13-VMSetUP.png">
</p>

<p>
Under the <b>Virtual network</b> setting, Azure automatically creates a new virtual network named <b>WiresharkAnalysis-vnet</b>. The subnet is configured as <b>10.0.0.0/24</b>, which defines the range of IP addresses available to devices inside this network.
</p>

<p>
The VM is also assigned a <b>Public IP address</b>, which allows us to connect to the virtual machine from outside the Azure environment using Remote Desktop.
</p>

<p>
Ensure that <b>Allow selected ports</b> is enabled and that <b>RDP (3389)</b> is selected. This allows remote connections to the Windows virtual machine.
</p>

<br>

<p>
<img width="1399" height="756" alt="Review and create virtual machine" src="images/14-VMSetUP.png">
</p>

<p>
After finishing the configuration settings, click the <b>Review + create</b> button. Azure will validate the virtual machine configuration to ensure that all required settings have been completed properly.
</p>

<br>

<p>
<img width="1399" height="756" alt="Validation passed and create VM" src="images/15-VMSetUP.png">
</p>

<p>
If the validation process passes successfully, Azure will display a confirmation message. Click the <b>Create</b> button to begin deploying the virtual machine.
</p>

<p>
Azure will now begin provisioning the Windows virtual machine and its associated resources, including the network interface, disk storage, and public IP address.
</p>

<br>

<p>
<img width="1399" height="756" alt="Deployment complete message" src="images/16-VMSetUP.png">
</p>

<p>
Once the deployment process is finished, Azure will display a message confirming that <b>Your deployment is complete</b>. This indicates that the Windows virtual machine has been successfully created.
</p>

<p>
At this point, the Windows VM is fully operational and ready to be used for the Wireshark packet analysis portion of this lab.
</p>

<br>

<p>
<img width="1399" height="756" alt="Searching for virtual machines in Azure" src="images/17-VMSetUP.png">
</p>

<p>
To verify that the virtual machine has been successfully deployed, return to the Azure search bar and type <b>virtual machines</b>. Select the <b>Virtual machines</b> service from the search results.
</p>

<br>

<p>
<img width="1399" height="756" alt="Virtual machines list showing running VM" src="images/18-VMSetUP.png">
</p>

<p>
You should now see the newly created virtual machine listed. The VM named <b>WiresharkAnalysis</b> should appear with a status of <b>Running</b>, indicating that the machine is active and ready for use.
</p>

<br>

<h3>Creating the Linux Virtual Machine</h3>

<p>
Next, we will create a second virtual machine that runs Linux. This machine will be used to generate network traffic that we can capture and analyze using Wireshark on the Windows machine.
</p>

<p>
Using two machines allows us to simulate real network communication between systems, which is necessary when analyzing protocols such as DHCP, DNS, ICMP, SSH, and RDP.
</p>

<br>

<p>
<img width="1399" height="756" alt="Create virtual machine menu" src="images/19-VMSetUP.png">
</p>

<p>
From the Virtual Machines page, click the <b>Create</b> button again and select <b>Virtual machine</b>. This will begin the process of creating the Linux virtual machine.
</p>

<br>

<p>
<img width="1399" height="756" alt="Linux virtual machine configuration" src="images/20-VMSetUP.png">
</p>

<p>
In the configuration page, select the same <b>Resource Group</b> used earlier in the lab. This keeps both virtual machines organized under the same project.
</p>

<p>
Give the machine a name such as <b>Linux-VM</b> and select the same <b>Central US</b> region that was used when creating the Windows virtual machine.
</p>

<p>
For the operating system image, choose <b>Ubuntu Server 24.04 LTS</b>. Ubuntu is a widely used Linux distribution and works well for generating network traffic and performing command-line network testing.
</p>

<p>
Most importantly, ensure that this Linux VM is connected to the <b>same Virtual Network</b> that was created earlier. This allows the Windows VM and Linux VM to communicate with each other inside the Azure environment.
</p>

<br>

<h3>Configuring Administrator Credentials for the Linux Virtual Machine</h3>

<p>
When creating the Linux virtual machine, we must configure administrator credentials. These credentials allow us to securely access and manage the system once it has been deployed.
</p>

<p>
Azure allows two authentication methods for Linux machines: <b>SSH Public Key</b> authentication or <b>Password</b> authentication. For this lab, we will use <b>Password authentication</b> because it is simpler for beginners and easier to demonstrate.
</p>

<p>
Enter a username and password that will be used to log into the Linux system.
</p>

<br>

<p>
<img width="1399" height="756" alt="Linux VM administrator credentials configuration" src="images/21-VMSetUP.png">
</p>

<p>
Under <b>Inbound port rules</b>, ensure that <b>Allow selected ports</b> is chosen and that <b>SSH (22)</b> is selected. SSH is the protocol used to securely connect to Linux systems remotely.
</p>

<p>
Allowing SSH access will let us log into the Linux virtual machine later to generate network traffic that Wireshark can capture and analyze.
</p>

---

<h3>Configuring Virtual Machine Disk Settings</h3>

<p>
Next, move to the <b>Disks</b> tab. This section defines the storage configuration for the virtual machine.
</p>

<p>
Every virtual machine requires an operating system disk where the system files and installed software will be stored.
</p>

<br>

<p>
<img width="1399" height="756" alt="Linux VM disk configuration" src="images/22-VMSetUP.png">
</p>

<p>
The default configuration uses a <b>Premium SSD</b> disk with approximately <b>30 GiB</b> of storage. This is more than sufficient for the purposes of this networking lab.
</p>

<p>
Since we do not need additional storage for this exercise, the default disk configuration can remain unchanged.
</p>

---

<h3>Configuring Networking for the Linux Virtual Machine</h3>

<p>
Next, navigate to the <b>Networking</b> tab. This is one of the most important sections for this lab.
</p>

<p>
Remember that both the Windows and Linux virtual machines must be placed inside the <b>same Virtual Network (VNet)</b>. This allows the machines to communicate with each other internally inside Azure.
</p>

<p>
Without being on the same virtual network, the machines would not be able to send traffic to each other, and Wireshark would not be able to capture the network packets that we will analyze later.
</p>

<br>

<p>
<img width="1399" height="756" alt="Linux VM networking configuration" src="images/23-VMSetUP.png">
</p>

<p>
Ensure that the selected virtual network is <b>WiresharkAnalysis-vnet</b>, which was created earlier when deploying the Windows virtual machine.
</p>

<p>
The Linux VM should also be assigned a <b>Public IP address</b>. This allows us to connect to the machine using SSH from outside the Azure environment.
</p>

<p>
Under <b>Inbound ports</b>, make sure <b>SSH (22)</b> is enabled so that remote SSH connections can be established.
</p>

---

<h3>Reviewing and Creating the Linux Virtual Machine</h3>

<p>
After completing all configuration steps, select the <b>Review + create</b> tab. Azure will automatically validate the configuration settings to ensure everything has been configured correctly.
</p>

<br>

<p>
<img width="1399" height="756" alt="Linux VM review and create page" src="images/24-VMSetUP.png">
</p>

<p>
If the validation passes successfully, Azure will display a confirmation message. At this point, click the <b>Create</b> button to begin deploying the Linux virtual machine.
</p>

<p>
Azure will now begin provisioning the Linux system along with its associated resources such as the disk, network interface, and public IP address.
</p>

---

<h3>Linux Virtual Machine Deployment</h3>

<p>
After clicking create, Azure begins the deployment process. During this time Azure allocates resources, configures networking, installs the operating system image, and prepares the machine for use.
</p>

<br>

<p>
<img width="1399" height="756" alt="Linux VM deployment in progress" src="images/25-VMSetUP.png">
</p>

<p>
This process typically takes a few minutes to complete depending on resource availability in the selected region.
</p>

---

<h3>Deployment Completion</h3>

<p>
Once the deployment finishes, Azure will display a message confirming that the deployment has completed successfully.
</p>

<br>

<p>
<img width="1399" height="756" alt="Linux VM deployment complete" src="images/26-VMSetUP.png">
</p>

<p>
At this point, the Linux virtual machine is fully operational inside the Azure cloud environment.
</p>

---

<h3>Verifying Both Virtual Machines</h3>

<p>
To verify that both machines were created successfully, return to the Azure search bar and type <b>VM</b>. Select the <b>Virtual machines</b> service from the search results.
</p>

<br>

<p>
<img width="1399" height="756" alt="Searching for virtual machines in Azure portal" src="images/27-VMSetUP.png">
</p>

<p>
This will open the Virtual Machines dashboard where all deployed machines can be viewed and managed.
</p>

<br>

<p>
<img width="1399" height="756" alt="Both Windows and Linux virtual machines running" src="images/28-VMSetUP.png">
</p>

<p>
You should now see both virtual machines listed and running:
</p>

<ul>
<li><b>WiresharkAnalysis</b> – Windows virtual machine</li>
<li><b>Linux-VM</b> – Ubuntu Linux virtual machine</li>
</ul>

<p>
Both machines are located in the same <b>Resource Group</b> and are connected to the same <b>Virtual Network</b>, which allows them to communicate with each other across the network.
</p>

<p>
This network communication will allow us to generate and analyze traffic using Wireshark in the next section of the lab.
</p>

---

<h2>End of Part 1</h2>

<p>
At this stage, we have successfully built a cloud-based networking lab environment using Microsoft Azure.
</p>

<p>
In <b>Part 2</b>, we will:
</p>

<ul>
<li>Connect to the Windows virtual machine using <b>Remote Desktop Protocol (RDP)</b></li>
<li>Install <b>Wireshark</b></li>
<li>Begin capturing and analyzing real network traffic</li>
</ul>

<p>
This environment will be used in later sections to analyze protocols including:
</p>

<ul>
<li>DHCP</li>
<li>DNS</li>
<li>ICMP</li>
<li>SSH</li>
<li>RDP</li>
</ul>

