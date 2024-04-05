Activity Log for Geom99 Practical LAb 4 Asnn

Creating a Virtual MAchine and firewall rules
Importance: High 
March 2nd 2024
Duration: 15 Minutes
1) Log onto google cloud through your gmail account 
2) Created GCP Project with name "MyFirstProject"
3) Opened the Compute Engine Console and clicked "Virtual Machine"
4) Started the "Create Instance" process and proceeded with the following Steps

   #Settings for the Instance
   1) Named the VM "arcgisserverinstance"
   2) set the location of the cloud to Iowa
   3) Machine configuration was set to e2-medium(2 VCPU/ 4GB memory)
   4) Under "Boot Disk" settings, change the default image by clicking"Change" and select "Custom Image" then"All" to select the project created by Shawn Morgan "geom99-2024-v1"
   5) Enable Firewall to allow both HTTP Traffic and HTTPS traffic.
   6) Click Create virtual Machien (will take a few minutes to boot up)
   7) once completed, clickt the drop down menu icon beside the RDP and select " Set Windows PAssword"
   8) Change username to student for this assignment, click next and recive the password will not be shown again so make sure to record it somewhere.  If unable to retrieve password then it can be reset as well by re-running this process.


   Setting up the FirewallL 5 Minutes
This process allows the google cloud to access the ports for ArcGIS Server Management
   1)Open Firefall  under VPC Network and Click "Create Firewall Rule"
   2) Name firewall rule as per instructions "flemingrdp444" but for future reference any name would be acceptable
   3) For "Targets" select  all instances in the network
   4)for Source Filter,  select IPV4 ranges
   5) for IP's the most restrictive IP would be preferred (home computer IP) but can also do 0.0.0.0/0 as this is the least restrictive IP Address and will allow for any computer to access.  Best to start with the least restrictive IP Address and switch to a more restricve IP when things are up and running smoothly.
   6) set the TCP port to "444"
   7) Click Save
   8) Create a new firewall rule and save it "arcgisserveradmin", same steps as above but set the TCP ports to "6443,6080".  ArcGIS wouldn't usually allow access with port 6080 but the provided virtual machine has been configured to do so for testing purposes
   9) Click Save

  Setting a windows firewall rule to allow ARCGis Server Management Ports 
  
1) find the extenral IP number from the GCP compute engine console and click on "copy IP"
2) only local desktop, click the windows icon on the bottom left hand corner and type in  "remote desktop Connection" and paste the copied IP address with the addition of :444 at the end for specifying the port number
3) When entering credentials, make sure you can type in for both dialog boxes.  If not then select "More Choices"
4) for username type in "Student" and for password paste in the password for the virtual machine and click "ok"
5) if the pop up "the identity of the remote computer cannot be verified.  Do you want to continue anyway? "  Click yes, as we know the identity and it can be trusted.
6) ensure to shut down the VM machine by clicking "stop Virtual machine" in the console.  If you forget this step, the machine will continue to run and you will continue to be charged.

7) 

Setting a windows Firewall rule to allow for server management ports
1) once in your virtual machine, click start and type in "windows defender firewall with advanced seccurity"
2) on the left hand side, click "inbound rules"  and select "new rule"
3) when the new rule box opens, click "port"  for rule type and click next
4) click  "TCP" and apply to to specific ports,  type in "6443,6080"
5) the default "allow all connections" will be fine for this project
6) name the rule ArcGIS Server Admin Ports" and click finish

This firewall rule will persist even after turning off the VM and will have to be recreated every time 


Publishing a Map server onto a GCP
Date: March 2nd 2024
Importance: Medium
Total time: 10 Minutes
1) Open up the Remote Desktop with the External IP and password
2) in your remote desktop, place the unzupped canada folder (folder can be found in the repository under "Canada") into the gisworkspace folder in the C drive on the virtual machine.
3) on your local desktop open up ArcGIS Pro and create a server connection to your server
4) go to Insert -->new connection-->add server-->New ArcGIS Server
5) For Server url type in "https://(externalIP):6443/arcgis
6) ignore the warning about the certificate, we know and trust the source so it shouldn't be an issue
7) Username is "siteadmin" and the password to the server was on the provided sheet my Shawn Morgan
8) don't bother saving credentials, the ip address will be changing constantly and
9) click finish and create server connection
10) from there add in the canada.shp file (this .shp file MUST be kept in the same folder path as the server, so it must be on your local computer in c/gisworkspace/canada/canada.shp, this is to ensure you aren't copying the data twice and overloading the server)
11) once the .shp file is on Pro, right click on the server on the right hand side in the catalog box and click on publish-->publish Map service
12) 


  
      
