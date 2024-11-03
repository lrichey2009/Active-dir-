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

<img src="./media/image2.png" style="width:5.83333in;height:3.08333in"
alt="Image 2" />

Step \#3

In my previous labs while working with other vm’s, I’ve discovered that
it may be of benefit for user’s experience to access your “settings” and
make a few changes before starting the actual virtual machine. You can
enable drag and drop with direction specification in “Advanced” \>
“Clipboard” \> “Drag and Drop” \> “Bi-directional” by having made this
change we will be able to drag and drop files from virtual machine over
to host machine and even reverse.

<img src="./media/image3.png" style="width:5.83333in;height:4.34375in"
alt="Image 1" />

Step \#4

After the vm has been set up click the finish button to initialize. For
this vm we will be operating with two network adapters. The first
adapter will be connected to the external internet, the other links to
the private network.

- Adapter 1 - NAT/Internet

- Adapter 2 – Intnet/Private network

<img src="./media/image4.png" style="width:5.83333in;height:4.39583in"
alt="Image 1" />
<img src="./media/image5.png" style="width:5.83333in;height:4.40625in"
alt="Image 2" />

Step \#5

We are ready to power on our virtual machine, the Operating System Set
up window will appear. We can advance pass this part by selecting “Next”
followed by “install Now” to begin the OS Install.

<img src="./media/image6.png" style="width:5.83333in;height:3.28125in"
alt="Image 1" /><img src="./media/image7.png" style="width:5.83333in;height:2.88542in"
alt="Image 2" />

Step \#6

Out of the four possible choices we will go with the “Desktop experience
which uses the GUI version of windows server 2022, the standard
evaluation”. This is the second option for us in the drop down.

<img src="./media/image8.png" style="width:5.83333in;height:3.91667in"
alt="Image 1" />

Step \#7

After making sure we’ve checked the box for “Microsoft Software License
Terms”, click next this is a free installation so we will choose the
“custom” option. We should then utilize “Drive0 unallocated space” to
load system files.

<img src="./media/image9.png" style="width:5.83333in;height:3.90625in"
alt="Image 1" />
<img src="./media/image10.png" style="width:5.83333in;height:3.90625in"
alt="Image 2" />

<img src="./media/image11.png" style="width:5.83333in;height:3.90625in"
alt="Image 1"/>

Step \#8

The server installation will begin and usually takes a few mins to
finalize. Once done the server will automatically reboot thus adjusting
configurations and implementing the correct settings.

<img src="./media/image12.png" style="width:5.83333in;height:3.90625in"
alt="Image 2" />

Step \#9

Be advised that when accessing vm logon screen the typical way we unlock
the system may be disabled. In this case we will use a feature that is
built into the virtual machine. Navigate to “Input” \> keyboard” and
choose “Insert ctrl +Alt +Del” this opens the system and enables us to
continue.

<img src="./media/image13.png" style="width:5.83333in;height:3.97917in"
alt="Image 1" />

Step \#10

Post successful login we will configure “Vm Guest Additions”. This
feature allows us to enhance the user experience by altering the
settings that control mouse lag and screen orientation. Click “Devices”
\> “insert Guest Additions CD Image”, find the file named “VBOX Windows
Additions- AMD 64”. After installation remember to reboot the system to
allow for changes to render true.

<img src="./media/image14.png" style="width:5.83333in;height:4.04167in"
alt="image 2" />
<img src="./media/image15.png" style="width:5.83333in;height:3.90625in"
alt="Image 2" />

<img src="./media/image16.png" style="width:5.83333in;height:3.54167in"
alt="Image 1" />

Step \#11

Now for the two network adapter configurations that must be set
accurately for proper communication to take place between systems. We
will need to go to the “settings” \> “Network and Internet” \> “Select
change adapter options”. Ethernet0 will receive its Ip Address from the
router. The Ip that was given to me was 10.0.2.15 /24, this adapter will
be the External network.

<img src="./media/image17.png" style="width:5.83333in;height:2.8125in"
alt="Image 2" />
<img src="./media/image18.png" style="width:5.83333in;height:3.29167in"
alt="Image 2" />

Step \#12

The internal network will be configured using the address range
“172.16.0.0 /24”. The server’s Ip will be set to 172.16.0.1, subnet mask
of 255.255.255.0. Eventually the server Ip will become the “Domain
Controller” and will act as the default gateway itself, we can obviously
leave that field blank. For DNS we can assign a loopback address of
127.0.0.1, we need to make sure that we are able to \[ping\] ourselves.

<img src="./media/image19.png" style="width:5.83333in;height:3.03125in"
alt="Image 2" />
<img src="./media/image20.png" style="width:5.83333in;height:3.04167in"
alt="Image 1" />

Step \#13

We’ve just completed Ip configurations, now we find “Server Manager”
there we will be able to update the “Local Server”. “Time Zone” to our
location isn’t necessary but ensuring that our server time and date
settings are accurate will be crucial to the system.

<img src="./media/image21.png" style="width:5.83333in;height:2.09375in"
alt="Image 2" />

Step \#14

Let’s rename our server to “DC” for simplicity, this gesture is to
compliment the fact that the server will be acting as the domain
controller as well. After renaming we will restart the server to load
the new changes.

<img src="./media/image22.png" style="width:5.83333in;height:2.73958in"
alt="Image 1" />

This was the final step in the AD set up right before we start
configuring roles and features, I would like to verify that all changes
thus far have been successfully implemented. At this point creating a
snapshot for insurance’s sake would be smart. I like to do this at
certain points in a project to serve as a place holder in the event
something happens to that main machine, we can revert to another one
that’s ready to go.

<img src="./media/image23.png" style="width:5.83333in;height:3.1875in"
alt="Image 2" />

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

<img src="./media/image24.png" style="width:5.83333in;height:2.77083in"
alt="Image 1" />

Step \#2

In the setup menu choose role based or feature based installation. This
option will add the role directly to the virtual machine and not
remotely or (VDI).

This is where we select our server “DC0” from the server pool list,
click next when ready.

<img src="./media/image25.png" style="width:5.83333in;height:4.15625in"
alt="Image 2" />
<img src="./media/image26.png" style="width:5.83333in;height:4.15625in"
alt="Image 2" />

Step \#3

Click “Server roles” \> Select “Active Directory Domain Services” \>
“Add features”.

<img src="./media/image27.png" style="width:5.83333in;height:4.125in"
alt="Image 1" />
<img src="./media/image28.png" style="width:5.83333in;height:4.125in"
alt="Image 1" />

Then continue through wizard leaving “features” and “AD DS” to default.
Select “Next” \> “Confirmation” \> “Install” and begin the installation
process.

<img src="./media/image29.png" style="width:5.83333in;height:4.13542in"
alt="Image 2" />
<img src="./media/image30.png" style="width:5.83333in;height:4.13542in"
alt="Image 2" />

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

<img src="./media/image31.png" style="width:5.83333in;height:2.88542in"
alt="Image 2" />
<img src="./media/image32.png" style="width:5.83333in;height:4.27083in"
alt="Image 2" />

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

<img src="./media/image33.png" style="width:5.83333in;height:4.28125in"
alt="Image 1" />
<img src="./media/image34.png" style="width:5.83333in;height:4.26042in"
alt="Image 1" />

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

<img src="./media/image35.png" style="width:5.83333in;height:4.29167in"
alt="Image 2" />

We have successfully gathered all resources needed for Active Directory.
Let’s proceed to “install” listed under the “Pre- requisite check”. A
reboot will be needed to set up the newly created domain @”
mydomain.com”, To preserve data let’s take another snapshot after
successful completion.

<img src="./media/image36.png" style="width:5.83333in;height:4.29167in"
alt="Image 2" />
<img src="./media/image37.png" style="width:5.83333in;height:2.46875in"
alt="Image 2" />

<img src="./media/image38.png" style="width:5.83333in;height:3.4375in"
alt="Image 1" />

Installing RAS/NAT on Domain Controller:

Step \#1

RAS/NAT protocols will allow our windows 10 clients to connect to the
private virtual network, maintaining internet access through the domain
controller. “Server Manager” \> “Add new roles” \> click next until you
come across “server roles”, choose “Remote Access” as role. Next to
“role services” \> “Routing” \>” Add features”. From the “confirmation”
section, select “Install” to start the process.

<img src="./media/image39.png" style="width:5.83333in;height:4.14583in"
alt="Image 1" /><img src="./media/image40.png" style="width:5.83333in;height:3.15625in"
alt="Image 2" />

<img src="./media/image41.png" style="width:5.83333in;height:4.14583in"
alt="Image 1" />

Step \#2

Alright, continuing the set up in “Server Manager” \> “Tools” \>
“Routing and Remote Access”. Right click your DC “Configure and Enable
Routing and Remote Access”. You will be guided by prompt. Once you’ve
selected next, select “Network Address Translation”. Where you see NAT
internal connection, you will simply pick connection with the internet
access. Click next, then finish. RAS/NAT are installed on the DC.

<img src="./media/image42.png" style="width:5.83333in;height:2.80208in"
alt="Image 2" />
<img src="./media/image43.png" style="width:5.83333in;height:4.33333in"
alt="Image 1" />

<img src="./media/image44.png" style="width:5.83333in;height:4.33333in"
alt="Image 2" />

Setting Up A DHCP Server:

Step \#1

Setting up the DHCP Server on our domain controller will allow us the
ability to automatically assign the windows 10 machines an Ip address.
Both the Intranet and Internet will be available to users. Open “Server
Manager” \> “Add new roles and features”. Select next to get through the
prompts, then “Server roles” \> “Remote Access” \> “Add features”\> Now
we approve and install.

<img src="./media/image45.png" style="width:5.83333in;height:2.69792in"
alt="Image 2" />
<img src="./media/image46.png" style="width:5.83333in;height:4.14583in"
alt="Image 2" />

<img src="./media/image47.png" style="width:5.83333in;height:4.14583in"
alt="Image 1" />

Step \#2

The DHCP scope is usually used to avoid Ip Address conflicts. This
seemed like a need to know. I will include the range of 172.16.0.100 –
172.16.0.200 with the subnet of 255.55.255.0. In “Server Manager” click
“tools” option. Find the drop-down menu select “DHCP” for DHCP server
options. Expand the DHCP server by right clicking “IPV4” within the
context menu, go to “New Scope” to configure our range. Click next to
set a “Scope Name”, the Ip range previously stated will serve us here.

<img src="./media/image48.png" style="width:5.83333in;height:3.57292in"
alt="Image 2" />

We will set the start Ip Address at 172.16.0.100 and the end Ip Address
at 172.16.0.200 with length of 24 or subnet mask 255.255.255.0

<img src="./media/image49.png" style="width:5.83333in;height:3.57292in"
alt="Image 1" />

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

<img src="./media/image50.png" style="width:5.83333in;height:3.72917in"
alt="Image 2" />
<img src="./media/image51.png" style="width:5.83333in;height:3.6875in"
alt="Image 1" />

<img src="./media/image52.png" style="width:5.83333in;height:3.41667in"
alt="Image 2" />

Adding Domain Users:

Step \#1

\# Method 1 creating Domain users Manually. \#

For new domain user creations, we will need to access the “Server Dash”
\> “Tools” \> “Active Directory Users and Computers”. Through ADUC right
click the domain name. “mydomain.com” select “New” and “User”

<img src="./media/image53.png" style="width:5.83333in;height:2.51042in"
alt="Image 2" />
<img src="./media/image54.png" style="width:5.83333in;height:4.60417in"
alt="Image 1" />

Step \#2

Fill out the fields with your example user data. Set a password and
remember to prompt user on next start up to change their password if you
like completely (optional) for lab.

<img src="./media/image55.png" style="width:4.53125in;height:3.9375in"
alt="Image 2" />
<img src="./media/image56.png" style="width:4.53125in;height:3.9375in"
alt="Image 2" />

<img src="./media/image57.png" style="width:4.53125in;height:3.9375in"
alt="Image 2" />

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

<img src="./media/image58.png" style="width:5.83333in;height:3.86458in"
alt="Image 2" />

For ease of use and added features this is the best choice for
operations. Since it’s just a lab we can say “User” is who’s using the
pc, and no password is required at this point.

<img src="./media/image59.png" style="width:5.83333in;height:3.86458in"
alt="Image 2" />

Next, we run Ipconfig in the cmd prompt. To check the DNS server’s
connectivity, I Pinged google.com ensuring operational status up to the
domain controller. (NAT) has done its job as well, the DC forwarded
traffic to the internet and allowed an echo reply to us (resulted as
expected).

<img src="./media/image60.png" style="width:5.83333in;height:3.03125in"
alt="Image 2" />

Finally, we are going to rename the pc and join the domain group. Right
click the start menu, select “System” find the option under the name
“Rename the pc (Advanced)” click on it. You will come to “system
properties” click “change” in the “computer Name/Domain changes” field
enter “client1” as the new pc name. Select “Domain” and type
“mydomain.com” as the domain. Add changes by clicking ok. We should
ensure that we’ve provided the correct admin credentials and finally a
quick restart to complete the domain join project.

<img src="./media/image61.png" style="width:5.83333in;height:4.26042in"
alt="Image 1" /><img src="./media/image62.png" style="width:5.83333in;height:4.26042in"
alt="Image 2" />

Head on over to the “Address leases” section of the DHCP scope then
domain controller, there we see client1 is now listed. Once the computer
was added to the network it received its Ip automatically.

<img src="./media/image63.png" style="width:5.83333in;height:3.40625in"
alt="Image 1" />

Conclusion, labs such as this one can enable entry level help desk
service techs to grow their skills at a steady pace. By helping them to
understand concepts and navigation of the Windows AD environment. It is
a good way to add experience to a resume and stand out amongst others
competing for the job. I believe that upskilling and showing you have
the drive and motive to be better every day is what helps make an
excellent IT specialist!

GOD Bless All!
