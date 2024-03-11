Activity Log for Geom99 Practical LAb 4 Asnn

Part 1 Total Time 5 Minutes
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
   2) Name firewall rule as per instructions "arcgisserveradmin" but for future reference any name would be acceptable
   3) For "Targets" select  all instances in the network
   4)for Source Filter,  select IPV4 ranges
   5) for IP's the most restrictive IP would be preferred (home computer IP) but can also do 0.0.0.0/0 as this is the least restrictive IP Address and will allow for any computer to access.  Best to start with the least restrictive IP Address and switch to a more restricve IP when things are up and running smoothly.
   6) Set the TCP ports to open 6443 and 6080.  ArcGIS wouldn't usually allow access with port 6080 but the provided virtual machine has been configured to do so for testing purposes
   7) Click Save
  

Interacting with the virutal Desktop

1) find the extenral IP number from the GCP compute engine console and click on "copy IP"
2) only local desktop, click the windows icon on the bottom left hand corner and type in  "remote desktop Connection" and paste the copied IP address with the addition of :444 at the end for specifying the port number
3) When entering credentials, make sure you can type in for both dialog boxes.  If not then select "More Choices"
4) for username type in "Student" and for password paste in the password for the virtual machine and click "ok"
5) if the pop up "the identity of the remote computer cannot be verified.  Do you want to continue anyway? "  Click yes, as we know the identity and it can be trusted.

6) Shut down VM when done



  
      
