------ Creating Key Pairs -----
1/ Create your key pairs if you don't have any:
	a/ Go EC2
	b/ On left pan: "Key Pairs"
	c/ Create Key Pair
	d/ Enter the name you want then create


------ Elastic IPs -----
3/ Create 2 Elastic IPs, one for the NAT Gateway and one for the BASTION
	a/ Go to "Service"
	b/ In left pan select "Elastic IPs"
	c/ Select "Allocate new address" (in new opened window, just choose "Allocate" then "close")


------ Create your VPC ---------	
4/ In the AWS Management Console, on the Services menu, click VPC.
5/ Click Start VPC Wizard.
6/ In the navigation pane, click VPC with Public and Private Subnets.
7/ Click Select.
8/ Configure the following settings (and ignore any settings that aren't listed):
	a/ IPV4CIDR block: Type: 10. 0. 0. 0/16
	b/ VPC name: "AWS Project 1"
	c/ Public subnet's IPv4 CIDR: Type 10. 0. 1. 0/24 
	d/ Availability Zone: Click the first Availability Zone.
	e/ Public subnet name: type "Public Subnet"
	f/ Private subnet's IPv4 CIDR: Type 10. 0. 3. 0/24
	g/ Availability Zone: Click the first Availability Zone. The same as used for "Public Subnet"
	h/ Private subnet name: type "Private Subnet"
	i/ Specify the details of your NAT gateway: "Choose one of the Elastic IP previously defined"
9/	Click Create VPC.
10/	In the success message, click OK.


------- Create Security Group for public subnet -----
11/ In the navigation pane, click Security Groups.
12/ Click Create Security Group.
13/ In the Create Security Group dialog box, configure the following settings (and ignore
	any settings that aren't listed)
	a/ Name tag: "AWS Project 1 public security group"
	b/ Group name: "AWS Project 1 public security group"
	c/ Description: "AWS Project 1 public security group"
	d/ VPC: Click "AWS Project 1" 
14/ Click Yes, Create.
15/ Select "AWS Project 1 public security group".
16/ Click the Inbound Rules tab.
17/ Click Edit.
18/ Click Add.
19/ For Type, click HTTP (80)
20/ Click in the Source "Anywhere"
21/ Click Add again.
22/ For Type, click HTTPS (443)
23/ Click in the Source "Anywhere"
24/ Click Add again.
25/ For Type, click SSH (22)
26/ Click in the Source "Anywhere"
27/ Click Save.


------- Create Security Group for private subnet -----
28/ Click again on Create Security Group.
29/ In the Create Security Group dialog box, configure the following settings (and ignore
	any settings that aren't listed)
	a/ Name tag: "AWS Project 1 private security group"
	b/ Group name: "AWS Project 1 private security group"
	c/ Description: "AWS Project 1 private security group"
	d/ VPC: Click "AWS Project 1" 
30/ Click Yes, Create.
31/ Select "AWS Project 1 public security group".
32/ Click the Inbound Rules tab.
33/ Click Edit.
34/ Click Add.
35/ For Type, click SSH (22)
36/ Click in the Source "Anywhere"
37/ Click Save.


------- Create WEBSERVER Instance ------
38/ On the Services menu, click EC2.
39/ Click Launch Instance.
40/ In the row for Amazon Linux AM
41/ On the Step 2: Choose an Instance Type page, confirm thet t2. micro is selected and then click Next: Configure Instance Details.
42/ On the Step 3: Configure Instance Details page, configure the following settings (and ignore any settings that aren't listed)
43/ Click Next: Add Storage.
44/ Click Next: Add Tags.
45/ Click Add Tag, and configure the following settings (and ignore any settings that aren't listed):
	a/ Key: "Name"
	b/ Value: "AWS Project 1 WEBSERVER"
46/ Click Next: Configure Security Group.
47/ On the Step 6: Configure Security Group page, click Select an existing security group, and then select the security group you created previously "AWS Project 1 private security group"
48/ Click Review and Launch. When prompted with a warning that you will not be able to connect to the instance through port 2 click Continue.
49/ Review the instance information and click Launch. Ignore any warning that appears regarding a security group being open to the world. This is expected behavior.
	
	
------- Create BASTION Instance ------
50/ On the Services menu, click EC2.
51/ Click Launch Instance.
52/ In the row for Amazon Linux AM
53/ On the Step 2: Choose an Instance Type page, confirm thet t2. micro is selected and then click Next: Configure Instance Details.
54/ On the Step 3: Configure Instance Details page, configure the following settings (and ignore any settings that aren't listed)
55/ Click Next: Add Storage.
56/ Click Next: Add Tags.
57/ Click Add Tag, and configure the following settings (and ignore any settings that aren't listed):
	a/ Key: "Name"
	b/ Value: "AWS Project 1 BASTION"
58/ Click Next: Configure Security Group.
59/ On the Step 6: Configure Security Group page, click Select an existing security group, and then select the security group you created previously "AWS Project 1 public security group"
60/ Click Review and Launch. When prompted with a warning that you will not be able to connect to the instance through port 2 click Continue.
61/ Review the instance information and click Launch. Ignore any warning that appears regarding a security group being open to the world. This is expected behavior.
62/ Assiciate your second Elastic IP you have created previously to your BASTION to connect it from external

		
---- Connect to your BASTION then to your WEBSERVER and ping google.com -----
63/ Open the windows "Power Shell" or "Ubuntu Shell"
64/ Go into the directory where you have your "PEM" key
65/ Copy your PEM key in your BASTION using scp: scp -i "Your_PEM_Key" Your_PEM_Key Your_Public_BASTION_IP  
65/ Connect to your BASTION using SSH, tape in your shell: ssh -i "Your_PEM_Key" Your_Public_BASTION_IP
66/ Once connected on your BASTION connect to your WEBSERVER using SSH: ssh -i "Your_PEM_Key" Your_Private_WEBSERVER_IP
67/ And ping google: ping google.com or ping 8.8.8.8

That's ALL!

		
