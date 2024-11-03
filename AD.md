A Windows Active Directory How-To Set Up:

Introduction: Step \#1

This is my brief presentation on how to set up windows server version
2022.

1.  To begin with you you will need the following: Virtualization
    software, I have opted to go with Oracle VirtualBox + Oracle Vm
    VirtualBox extension pack, since it’s all-free download.

2.  Windows Server 2022, I simply downloaded a copy from the Microsoft
    evaluation Centre.

3.  Windows 10. A quick visit over to Microsoft.com to grab this iso
    file for download.

I’ve started by clicking on Oracle VirtualBox and selecting “New” to
create a new machine. I then selected my windows server “iso file” that
I downloaded earlier. Feel free to “skip the unattended install to
quicken the process.
![media_image1](https://github.com/user-attachments/assets/c990a7d3-26bb-471e-af2b-c2eeef331aa2)


Hardware Specifications:

Step \#2

- Processors: 2

- RAM: 2 GB

- Disk Size: A minimum of 20 GB

![media_image2](https://github.com/user-attachments/assets/8c4e32c4-5bd2-4486-a97d-458d25fc3f04)

Step \#3

In my previous labs while working with other vm’s, I’ve discovered that
it may be of benefit for user’s experience to access your “settings” and
make a few changes before starting the actual virtual machine. You can
enable drag and drop with direction specification in “Advanced” \>
“Clipboard” \> “Drag and Drop” \> “Bi-directional” by having made this
change we will be able to drag and drop files from virtual machine over
to host machine and even reverse.

![media_image3](https://github.com/user-attachments/assets/015cb3a9-f14f-42fd-9a6a-dad7c0edb674)

Step \#4

After the vm has been set up click the finish button to initialize. For
this vm we will be operating with two network adapters. The first
adapter will be connected to the external internet, the other links to
the private network.

- Adapter 1 - NAT/Internet

- Adapter 2 – Intnet/Private network

![media_image4](https://github.com/user-attachments/assets/c42db00e-1213-4782-bfc8-c511bb60cbbe)
![image5](https://github.com/user-attachments/assets/3527d34a-e694-497a-8548-67f972940707)

Step \#5

We are ready to power on our virtual machine, the Operating System Set
up window will appear. We can advance pass this part by selecting “Next”
followed by “install Now” to begin the OS Install.

![image6](https://github.com/user-attachments/assets/5fcbbdfc-6026-4f6a-8d74-2bc0c99c5642)![image7](https://github.com/user-attachments/assets/46639d04-48a2-4137-8061-4d1ad3533069)


Step \#6

Out of the four possible choices we will go with the “Desktop experience
which uses the GUI version of windows server 2022, the standard
evaluation”. This is the second option for us in the drop down.

![image8](https://github.com/user-attachments/assets/14044ddf-56aa-4a9d-a749-c628a1f79ed2)

Step \#7

After making sure we’ve checked the box for “Microsoft Software License
Terms”, click next this is a free installation so we will choose the
“custom” option. We should then utilize “Drive0 unallocated space” to
load system files.

![image9](https://github.com/user-attachments/assets/8ec2ca06-759f-4f86-82ab-11146d0343c6)
![image10](https://github.com/user-attachments/assets/a54278a1-a9da-445b-a23c-2359ea6bf258)

![image11](https://github.com/user-attachments/assets/573237d5-db16-420e-b893-1a9c4335bf62)

Step \#8

The server installation will begin and usually takes a few mins to
finalize. Once done the server will automatically reboot thus adjusting
configurations and implementing the correct settings.

![image12](https://github.com/user-attachments/assets/49d7edd7-f129-4b40-baad-e7647855b201)

Step \#9

Be advised that when accessing vm logon screen the typical way we unlock
the system may be disabled. In this case we will use a feature that is
built into the virtual machine. Navigate to “Input” \> keyboard” and
choose “Insert ctrl +Alt +Del” this opens the system and enables us to
continue.

![image13](https://github.com/user-attachments/assets/c4985271-a130-45fb-ae2c-95b1eb5fb894)

Step \#10

Post successful login we will configure “Vm Guest Additions”. This
feature allows us to enhance the user experience by altering the
settings that control mouse lag and screen orientation. Click “Devices”
\> “insert Guest Additions CD Image”, find the file named “VBOX Windows
Additions- AMD 64”. After installation remember to reboot the system to
allow for changes to render true.

![image14](https://github.com/user-attachments/assets/3c01e7c3-f09b-4d3b-8d81-5242a94e9072)
![image15](https://github.com/user-attachments/assets/1b4931bc-fc49-4eb2-8443-5291ef0a33c5)

![image16](https://github.com/user-attachments/assets/bea53448-8a7b-4665-b6bc-ff500e36e48b)

Step \#11

Now for the two network adapter configurations that must be set
accurately for proper communication to take place between systems. We
will need to go to the “settings” \> “Network and Internet” \> “Select
change adapter options”. Ethernet0 will receive its Ip Address from the
router. The Ip that was given to me was 10.0.2.15 /24, this adapter will
be the External network.

![image17](https://github.com/user-attachments/assets/64df1fa9-f1e4-4ebe-84a4-74a0d494408e)
![image18](https://github.com/user-attachments/assets/90f007ca-138a-4cc4-95ad-b6d4a16a17be)

Step \#12

The internal network will be configured using the address range
“172.16.0.0 /24”. The server’s Ip will be set to 172.16.0.1, subnet mask
of 255.255.255.0. Eventually the server Ip will become the “Domain
Controller” and will act as the default gateway itself, we can obviously
leave that field blank. For DNS we can assign a loopback address of
127.0.0.1, we need to make sure that we are able to \[ping\] ourselves.

![image19](https://github.com/user-attachments/assets/a7f23c02-5da8-47b8-896d-a0255c02fa60)
![image20](https://github.com/user-attachments/assets/d4a2bbd4-b844-4c14-9d21-598f90a32c50)


Step \#13

We’ve just completed Ip configurations, now we find “Server Manager”
there we will be able to update the “Local Server”. “Time Zone” to our
location isn’t necessary but ensuring that our server time and date
settings are accurate will be crucial to the system.

![image21](https://github.com/user-attachments/assets/25a1ba76-74c3-4224-9019-a53a4ac7bff5)

Step \#14

Let’s rename our server to “DC” for simplicity, this gesture is to
compliment the fact that the server will be acting as the domain
controller as well. After renaming we will restart the server to load
the new changes.

![image22](https://github.com/user-attachments/assets/108d9ca2-c58f-4e1e-a7b0-96cbd0cfb6b4)

This was the final step in the AD set up right before we start
configuring roles and features, I would like to verify that all changes
thus far have been successfully implemented. At this point creating a
snapshot for insurance’s sake would be smart. I like to do this at
certain points in a project to serve as a place holder in the event
something happens to that main machine, we can revert to another one
that’s ready to go.

![image23](https://github.com/user-attachments/assets/7957229f-04dd-4dab-8536-137d46a6334b)

Configuring Active Directory Services:

Step \#1

Now to speak more in depth to the roles and features we plan to add.
These are vital active directory services, instrumental for the root
domain we will build and name “mydomain.org”.

Select “Add roles and features” in the dashboard.

In this project we will display the difference between roles and
features. The role will reflect the server’s specific assignment of
acting as a domain controller. Features will be resources used to
enhance settings. Capabilities such as administrative tools, AD DS
tools, Group Policy Management, will aid in user set up.

![image24](https://github.com/user-attachments/assets/545870c4-bf3f-4947-adc1-638e22f0ef66)

Step \#2

In the setup menu choose role based or feature based installation. This
option will add the role directly to the virtual machine and not
remotely or (VDI).

This is where we select our server “DC0” from the server pool list,
click next when ready.

![image25](https://github.com/user-attachments/assets/ebd4e253-fe23-4c8f-a091-be20c08cd491)
![image26](https://github.com/user-attachments/assets/84dc2e42-4504-4dce-bc17-2d2ae132670d)

Step \#3

Click “Server roles” \> Select “Active Directory Domain Services” \>
“Add features”.

![image27](https://github.com/user-attachments/assets/b0a99fb7-b1b4-4377-9ce5-e134c2e1b338)
![image28](https://github.com/user-attachments/assets/dec83ebe-9871-4d9c-83ed-b5a412103e1b)

Then continue through wizard leaving “features” and “AD DS” to default.
Select “Next” \> “Confirmation” \> “Install” and begin the installation
process.

![image29](https://github.com/user-attachments/assets/33db5b06-ca4f-4570-8c64-2227d6e80594)
![image30](https://github.com/user-attachments/assets/33ca92a2-65f4-493b-8a14-b91a3bf69998)

Step \#4

After the installation process has completed, a prompt will follow
asking if you would like to promote the server to “Domain Controller”.
We should opt to initiate the domain controller config. Select “Add a
new forest” and give it the name “mydomain.com”.

\# Forests are containers that hold objects and settings in an AD
environment. Child domain, users, systems, groups, policies are all
functions within a forest. Unless a trust relationship is established
between two forests, they will not be able to interact, this signifies
that each forest has a security boundary. \#

![image31](https://github.com/user-attachments/assets/eec3c5c4-fa0e-4a2f-97c9-8cce68075a04)
![image32](https://github.com/user-attachments/assets/a16e86eb-03e4-4fd0-9cd3-7968e4779ae8)

Step \#5

- Next ensure that the “Functional Forest level is placed on windows
  2016 (the highest level available). Choose a passcode for “Directory
  Services Restore Mode. (DSRM)

- The “DNS Option”. We won’t select to create DNS Delegation, instead we
  will continue by tapping the next button.

- The windows 2016 functional level supports the use of windows 2022 on
  the domain controller.

\# (DSRM) it is a special boot mode accessible only on the domain
controller when the AD fails. This function allows domain admin to log
into the DC using (DSRM) credentials. \#

\# (DA) Domain Admin uses safe mode to restore and repair objects within
the active directory database. \#

![image33](https://github.com/user-attachments/assets/f7af6643-f5e4-41c4-a589-c2fd38d4d9fc)
![image34](https://github.com/user-attachments/assets/e9063a52-a0cc-4400-9ffe-80367ca565ae)

Step \#6

Let’s confirm our NetBIOS domain name then select next to navigate to
“paths”. In this section we will find the Active Directory database.
Logfiles, (NTDS), SYSVOL can be located here. We will keep the default
paths so that no issue arises from that in the future, what’s next?

\# NTDS- this database houses Active Directory data, info on users,
computers, groups, and network resources. \#

\# SYSVOL- Folder that contains various public files, other folders and
other critical parts. GPO’s and Scripts help to correctly and accurately
manage computers and users that’s apart from a particular forest \#

![image35](https://github.com/user-attachments/assets/13bac496-f6da-4021-8856-5a433ebbbc5d)

We have successfully gathered all resources needed for Active Directory.
Let’s proceed to “install” listed under the “Pre- requisite check”. A
reboot will be needed to set up the newly created domain @”
mydomain.com”, To preserve data let’s take another snapshot after
successful completion.

![image36](https://github.com/user-attachments/assets/c966cca5-bd45-4f26-9469-58c64ecdeb5d)
![image37](https://github.com/user-attachments/assets/dd2b0096-2d72-464c-ae8f-912e653325ee)

![image38](https://github.com/user-attachments/assets/7efeb35e-c2b8-4873-891c-7fa2f5970bf8)

Installing RAS/NAT on Domain Controller:

Step \#1

RAS/NAT protocols will allow our windows 10 clients to connect to the
private virtual network, maintaining internet access through the domain
controller. “Server Manager” \> “Add new roles” \> click next until you
come across “server roles”, choose “Remote Access” as role. Next to
“role services” \> “Routing” \>” Add features”. From the “confirmation”
section, select “Install” to start the process.
![image39](https://github.com/user-attachments/assets/a6dcf48d-5a7d-4b54-a99a-ee42a5b69867)
![image40](https://github.com/user-attachments/assets/80c2db72-6607-4d57-9960-a2e3be353fa4)

![image41](https://github.com/user-attachments/assets/0621e61a-fe0d-4762-b578-94b4ea41f999)

Step \#2

Alright, continuing the set up in “Server Manager” \> “Tools” \>
“Routing and Remote Access”. Right click your DC “Configure and Enable
Routing and Remote Access”. You will be guided by prompt. Once you’ve
selected next, select “Network Address Translation”. Where you see NAT
internal connection, you will simply pick connection with the internet
access. Click next, then finish. RAS/NAT are installed on the DC.

![image42](https://github.com/user-attachments/assets/47075e62-d6db-454f-ad6d-b8cccc62ab9b)
![image43](https://github.com/user-attachments/assets/43742376-c4ba-4c8d-813e-da2d70b2c5c7)

![image44](https://github.com/user-attachments/assets/b5b1a5fe-2c8b-49ad-a96a-410e8ef2138a)

Setting Up A DHCP Server:

Step \#1

Setting up the DHCP Server on our domain controller will allow us the
ability to automatically assign the windows 10 machines an Ip address.
Both the Intranet and Internet will be available to users. Open “Server
Manager” \> “Add new roles and features”. Select next to get through the
prompts, then “Server roles” \> “Remote Access” \> “Add features”\> Now
we approve and install.

![image45](https://github.com/user-attachments/assets/3c55ed53-c0bd-434a-af97-de51c0a1ac91)
![image46](https://github.com/user-attachments/assets/5708c4c3-6b30-49f5-8224-e383503dc319)

![image47](https://github.com/user-attachments/assets/c0373585-fea2-4801-9eb2-4159916b45d6)

Step \#2

The DHCP scope is usually used to avoid Ip Address conflicts. This
seemed like a need to know. I will include the range of 172.16.0.100 –
172.16.0.200 with the subnet of 255.55.255.0. In “Server Manager” click
“tools” option. Find the drop-down menu select “DHCP” for DHCP server
options. Expand the DHCP server by right clicking “IPV4” within the
context menu, go to “New Scope” to configure our range. Click next to
set a “Scope Name”, the Ip range previously stated will serve us here.

![image48](https://github.com/user-attachments/assets/f1974509-74d0-4777-a998-2e04f5330b1f)

We will set the start Ip Address at 172.16.0.100 and the end Ip Address
at 172.16.0.200 with length of 24 or subnet mask 255.255.255.0

![image49](https://github.com/user-attachments/assets/4972f24f-df2d-4cb7-a20a-804f49235e98)

Step \#3

Once we have set the scope, we will encounter the “lease duration”
screen, leave the options default.

- Router (Default Gateway)- here we will enter the Ip Address of our DC
  which is 172.16.0.1 in the “Ip Address” space, finally click “Add” and
  “next”.

- Domain Name and DNS servers in the parent domain column enter
  “mydomain.com”. Since we will indeed be using our domain controller as
  a DNS server, select next to continue. Keep settings unchanged from
  now until we get to the end of the set-up wizard. Click finish to
  complete the DHCP Scope configuration.

Right click on DHCP server and “Authorize”. Right click once more to
ensure that you’ve refreshed so that the changes will take place.

![image50](https://github.com/user-attachments/assets/366a2297-9fec-49e1-b9b1-db0e68f2fa86)
![image51](https://github.com/user-attachments/assets/d199ea4e-240d-4b81-a46a-ef6e660437fe)

![image52](https://github.com/user-attachments/assets/5717d186-432c-4bd6-be60-b1d9d5fa1de9)

Adding Domain Users:

Step \#1

\# Method 1 creating Domain users Manually. \#

For new domain user creations, we will need to access the “Server Dash”
\> “Tools” \> “Active Directory Users and Computers”. Through ADUC right
click the domain name. “mydomain.com” select “New” and “User”

![image53](https://github.com/user-attachments/assets/c0ea7409-3641-457a-9f2e-61d7e05b9a72)
![image54](https://github.com/user-attachments/assets/2c05e206-cbb5-4010-b297-75c1e335e053)

Step \#2

Fill out the fields with your example user data. Set a password and
remember to prompt user on next start up to change their password if you
like completely (optional) for lab.

![image55](https://github.com/user-attachments/assets/1b9e186e-433f-44c7-96ca-5a8838c8ff88)
![image56](https://github.com/user-attachments/assets/3723b53f-02b2-4f92-a58d-4b626bc7ed32)

![image57](https://github.com/user-attachments/assets/125e532d-e83f-4e86-b7f0-e6443e69ec85)

Step \#3

We are looking at a full set up. A quick rundown of everything, the
network diagram should read as follows Internet connections, NICs,
domain with the user set up, NAT, DHCP, connected to the internal VBOX
network.

We still have a windows 10 machine to add to the VBOX Internal NIC. It
as well will receive its Ip Address automatically from over DHCP server.
Once we have set up that machine, we will confirm connection by running
a few ping tests across the networks.

Run the windows set up as we did before. You can use a name like
“Client1”. “Select operating system in the next field. We will opt with
“Windows 10 Pro”.

![image58](https://github.com/user-attachments/assets/2d1f6397-7851-4c91-84d8-e35dc0692953)

For ease of use and added features this is the best choice for
operations. Since it’s just a lab we can say “User” is who’s using the
pc, and no password is required at this point.

![image59](https://github.com/user-attachments/assets/72820919-161c-4e47-ad12-e0f2c14b08dd)

Next, we run Ipconfig in the cmd prompt. To check the DNS server’s
connectivity, I Pinged google.com ensuring operational status up to the
domain controller. (NAT) has done its job as well, the DC forwarded
traffic to the internet and allowed an echo reply to us (resulted as
expected).

![image60](https://github.com/user-attachments/assets/5d3f49a4-62ea-46b8-8e1f-f990d82d5e4b)

Finally, we are going to rename the pc and join the domain group. Right
click the start menu, select “System” find the option under the name
“Rename the pc (Advanced)” click on it. You will come to “system
properties” click “change” in the “computer Name/Domain changes” field
enter “client1” as the new pc name. Select “Domain” and type
“mydomain.com” as the domain. Add changes by clicking ok. We should
ensure that we’ve provided the correct admin credentials and finally a
quick restart to complete the domain join project.

![image61](https://github.com/user-attachments/assets/b08f2680-15d9-4cad-a595-7838ae7f36e9)![image62](https://github.com/user-attachments/assets/3463f70b-09e9-4657-9bab-c9bd0bb347b0)

Head on over to the “Address leases” section of the DHCP scope then
domain controller, there we see client1 is now listed. Once the computer
was added to the network it received its Ip automatically.

![image63](https://github.com/user-attachments/assets/0079861f-4f4d-4558-93a2-83b17fa9a400)


Conclusion, labs such as this one can enable entry level help desk
service techs to grow their skills at a steady pace. By helping them to
understand concepts and navigation of the Windows AD environment. It is
a good way to add experience to a resume and stand out amongst others
competing for the job. I believe that upskilling and showing you have
the drive and motive to be better every day is what helps make an
excellent IT specialist!

GOD Bless All!
