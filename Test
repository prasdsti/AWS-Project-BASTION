# AWS Project BASTION
------ Creating Key Pairs -----
1/ Create your key pairs if you don't have any:
	a/ Go EC2
	b/ On left pan: "Key Pairs"
	c/ Create Key Pair
	d/ Enter the name you want then create


------ Elastic IPs -----
2/ Create 2 Elastic IPs, one for the NAT Gateway and one for the BASTION
	a/ Go to "Service"
	b/ In left pan select "Elastic IPs"
	c/ Select "Allocate new address" (in new opened window, just choose "Allocate" then "close")


------ Create your VPC ---------	
3/ In the AWS Management Console, on the Services menu, click VPC.
4/ Click Start VPC Wizard.
5/ In the navigation pane, click VPC with Public and Private Subnets.
6/ Click Select.
7/ Configure the following settings (and ignore any settings that aren't listed):
	a/ IPV4CIDR block: Type: 10. 0. 0. 0/16
	b/ VPC name: "AWS Project 1"
	c/ Public subnet's IPv4 CIDR: Type 10. 0. 1. 0/24 
	d/ Availability Zone: Click the first Availability Zone.
	e/ Public subnet name: type "Public Subnet"
	f/ Private subnet's IPv4 CIDR: Type 10. 0. 3. 0/24
	g/ Availability Zone: Click the first Availability Zone. The same as used for "Public Subnet"
	h/ Private subnet name: type "Private Subnet"
	i/ Specify the details of your NAT gateway: "Choose one of the Elastic IP previously defined"
8/	Click Create VPC.
9/	In the success message, click OK.


------- Create Security Group for public subnet -----
10/ In the navigation pane, click Security Groups.
11/ Click Create Security Group.
12/ In the Create Security Group dialog box, configure the following settings (and ignore
	any settings that aren't listed)
	a/ Name tag: "AWS Project 1 public security group"
	b/ Group name: "AWS Project 1 public security group"
	c/ Description: "AWS Project 1 public security group"
	d/ VPC: Click "AWS Project 1" 
13/ Click Yes, Create.
14/ Select "AWS Project 1 public security group".
15/ Click the Inbound Rules tab.
16/ Click Edit.
17/ Click Add.
18/ For Type, click HTTP (80)
19/ Click in the Source "Anywhere"
20/ Click Add again.
21/ For Type, click HTTPS (443)
22/ Click in the Source "Anywhere"
23/ Click Add again.
24/ For Type, click SSH (22)
25/ Click in the Source "Anywhere"
26/ Click Save.


------- Create Security Group for private subnet -----
27/ Click again on Create Security Group.
28/ In the Create Security Group dialog box, configure the following settings (and ignore
	any settings that aren't listed)
	a/ Name tag: "AWS Project 1 private security group"
	b/ Group name: "AWS Project 1 private security group"
	c/ Description: "AWS Project 1 private security group"
	d/ VPC: Click "AWS Project 1" 
29/ Click Yes, Create.
30/ Select "AWS Project 1 public security group".
31/ Click the Inbound Rules tab.
32/ Click Edit.
33/ Click Add.
34/ For Type, click SSH (22)
35/ Click in the Source "Anywhere"
36/ Click Save.


------- Create WEBSERVER Instance ------
37/ On the Services menu, click EC2.
38/ Click Launch Instance.
39/ In the row for Amazon Linux AM
40/ On the Step 2: Choose an Instance Type page, confirm thet t2. micro is selected and then click Next: Configure Instance Details.
41/ On the Step 3: Configure Instance Details page, configure the following settings (and ignore any settings that aren't listed)
42/ Click Next: Add Storage.
43/ Click Next: Add Tags.
44/ Click Add Tag, and configure the following settings (and ignore any settings that aren't listed):
	a/ Key: "Name"
	b/ Value: "AWS Project 1 WEBSERVER"
45/ Click Next: Configure Security Group.
46/ On the Step 6: Configure Security Group page, click Select an existing security group, and then select the security group you created previously "AWS Project 1 private security group"
47/ Click Review and Launch. When prompted with a warning that you will not be able to connect to the instance through port 2 click Continue.
48/ Review the instance information and click Launch. Ignore any warning that appears regarding a security group being open to the world. This is expected behavior.
	
	
------- Create BASTION Instance ------
49/ On the Services menu, click EC2.
50/ Click Launch Instance.
51/ In the row for Amazon Linux AM
52/ On the Step 2: Choose an Instance Type page, confirm thet t2. micro is selected and then click Next: Configure Instance Details.
53/ On the Step 3: Configure Instance Details page, configure the following settings (and ignore any settings that aren't listed)
54/ Click Next: Add Storage.
55/ Click Next: Add Tags.
56/ Click Add Tag, and configure the following settings (and ignore any settings that aren't listed):
	a/ Key: "Name"
	b/ Value: "AWS Project 1 BASTION"
57/ Click Next: Configure Security Group.
58/ On the Step 6: Configure Security Group page, click Select an existing security group, and then select the security group you created previously "AWS Project 1 public security group"
59/ Click Review and Launch. When prompted with a warning that you will not be able to connect to the instance through port 2 click Continue.
60/ Review the instance information and click Launch. Ignore any warning that appears regarding a security group being open to the world. This is expected behavior.
61/ Assiciate your second Elastic IP you have created previously to your BASTION to connect it from external

		
---- Connect to your BASTION then to your WEBSERVER and ping google.com -----
62/ Open the windows "Power Shell" or "Ubuntu Shell"
63/ Go into the directory where you have your "PEM" key
64/ Copy your PEM key in your BASTION using scp: scp -i "Your_PEM_Key" Your_PEM_Key Your_Public_BASTION_IP  
65/ Connect to your BASTION using SSH, tape in your shell: ssh -i "Your_PEM_Key" Your_Public_BASTION_IP
66/ Once connected on your BASTION connect to your WEBSERVER using SSH: ssh -i "Your_PEM_Key" Your_Private_WEBSERVER_IP
67/ And ping google: ping google.com or ping 8.8.8.8

That's ALL!
