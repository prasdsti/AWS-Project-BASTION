------ Elastic IPs-----
1/ Create 2 Elastic IPs, one for the NAT Gateway and one for the BASTION
	a/ Go to "Service"
	b/ In left pan select "Elastic IPs"
	c/ Select "Allocate new address" (in new opened window, just choose "Allocate" then "close")


------ Create your VPC ---------	
5/ In the AWS Management Console, on the Services menu, click VPC.
6/ Click Start VPC Wizard.
7/ In the navigation pane, click VPC with Public and Private Subnets.
8/ Click Select.
9/ Configure the following settings (and ignore any settings that aren't listed):
	a/ IPV4CIDR block: Type: 10. 0. 0. 0/16
	b/ VPC name: "AWS Project 1"
	c/ Public subnet's IPv4 CIDR: Type 10. 0. 1. 0/24 
	d/ Availability Zone: Click the first Availability Zone.
	e/ Public subnet name: type "Public Subnet"
	f/ Private subnet's IPv4 CIDR: Type 10. 0. 3. 0/24
	g/ Availability Zone: Click the first Availability Zone. The same as used for "Public Subnet"
	h/ Private subnet name: type "Private Subnet"
	i/ Specify the details of your NAT gateway: "Choose one of the Elastic IP previously defined"
10/	Click Create VPC.
11/	In the success message, click OK.


------- Create Security Group for public subnet -----
12/ In the navigation pane, click Security Groups.
13/ Click Create Security Group.
14/ In the Create Security Group dialog box, configure the following settings (and ignore
	any settings that aren't listed)
	a/ Name tag: "AWS Project 1 public security group"
	b/ Group name: "AWS Project 1 public security group"
	c/ Description: "AWS Project 1 public security group"
	d/ VPC: Click "AWS Project 1" 
15/ Click Yes, Create.
16/ Select "AWS Project 1 public security group".
17/ Click the Inbound Rules tab.
18/ Click Edit.
19/ Click Add.
20/ For Type, click HTTP (80)
21/ Click in the Source "Anywhere"
22/ Click Add again.
23/ For Type, click HTTPS (443)
24/ Click in the Source "Anywhere"
25/ Click Add again.
26/ For Type, click SSH (22)
27/ Click in the Source "Anywhere"
28/ Click Save.


------- Create Security Group for private subnet -----
29/ Click again on Create Security Group.
30/ In the Create Security Group dialog box, configure the following settings (and ignore
	any settings that aren't listed)
	a/ Name tag: "AWS Project 1 private security group"
	b/ Group name: "AWS Project 1 private security group"
	c/ Description: "AWS Project 1 private security group"
	d/ VPC: Click "AWS Project 1" 
31/ Click Yes, Create.
32/ Select "AWS Project 1 public security group".
33/ Click the Inbound Rules tab.
34/ Click Edit.
35/ Click Add.
36/ For Type, click SSH (22)
37/ Click in the Source "Anywhere"
38/ Click Save.


------- Create WEBSERVER Instance ------
39/ On the Services menu, click EC2.
40/ Click Launch Instance.
41/ In the row for Amazon Linux AM
42/ On the Step 2: Choose an Instance Type page, confirm thet t2. micro is selected and then click Next: Configure Instance Details.
43/ On the Step 3: Configure Instance Details page, configure the following settings (and ignore any settings that aren't listed)
44/ Click Next: Add Storage.
45/ Click Next: Add Tags.
46/ Click Add Tag, and configure the following settings (and ignore any settings that aren't listed):
	a/ Key: "Name"
	b/ Value: "AWS Project 1 WEBSERVER"
47/ Click Next: Configure Security Group.
48/ On the Step 6: Configure Security Group page, click Select an existing security group, and then select the security group you created previously "AWS Project 1 private security group"
49/ Click Review and Launch. When prompted with a warning that you will not be able to connect to the instance through port 2 click Continue.
50/ Review the instance information and click Launch. Ignore any warning that appears regarding a security group being open to the world. This is expected behavior.
	
	
------- Create BASTION Instance ------
51/ On the Services menu, click EC2.
52/ Click Launch Instance.
53/ In the row for Amazon Linux AM
54/ On the Step 2: Choose an Instance Type page, confirm thet t2. micro is selected and then click Next: Configure Instance Details.
55/ On the Step 3: Configure Instance Details page, configure the following settings (and ignore any settings that aren't listed)
56/ Click Next: Add Storage.
57/ Click Next: Add Tags.
58/ Click Add Tag, and configure the following settings (and ignore any settings that aren't listed):
	a/ Key: "Name"
	b/ Value: "AWS Project 1 BASTION"
59/ Click Next: Configure Security Group.
60/ On the Step 6: Configure Security Group page, click Select an existing security group, and then select the security group you created previously "AWS Project 1 public security group"
61/ Click Review and Launch. When prompted with a warning that you will not be able to connect to the instance through port 2 click Continue.
62/ Review the instance information and click Launch. Ignore any warning that appears regarding a security group being open to the world. This is expected behavior.

		
	
		
