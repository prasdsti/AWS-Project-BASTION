------ NAT Creation for Elastic IPs-----
1/ Create a NAT gateway
2/ Open the Amazon VPC console at https://console.aws.amazon.com/vpc/.
3/ In the navigation pane, choose NAT Gateways, Create NAT Gateway.
4/ Specify the subnet in which to create the NAT gateway and select an Elastic IP address allocation ID to associate with the NAT gateway. When finished, choose Create a NAT Gateway. The NAT gateway appears in the console. After a few moments, her status changes to Available, after which she is ready to use.

------ Create your VPC ---------	
5/ In the AWS Management Console, on the Services menu, click VPC.
6/ Click Start VPC Wizard.
7/ In the navigation pane, click VPC with Public and Private Subnets.
8/ Click Select.
9/ Configure the following settings (and ignore any settings that aren't listed):
	a/ IPV4CIDR block: Type: 10. 0. 0. 0/16
	b/ VPC name: "AWS Project 1"
	c/ Public subnet's IPv4 CIDR: Type 10. 0. 1. 0/24 You can safely ignore the
		error: Public and private subnet CIDR blocks overlap. You will fix this when you
		change the value below.
	d/ Availability Zone: Click the first Availability Zone.
	e/ Public subnet name: type "Public Subnet 1"
	f/ Private subnet's IPv4 CIDR: Type 10. 0. 3. 0/24
	g/ Availability Zone: Click the first Availability Zone. The same as used for Public
		Subnet 1
	h/ Private subnet name: type "Private Subnet 1"
	i/ Specify the details of your NAT gateway: Click Use a NAT instance instead. On
		the far right of the screen-you may need to scroll.
	j/ Key pair name: Click the Qwiklabs key pair.
10/	Click Create VPC.
11/	In the success message, click OK.

------- Create Security Group -----
12/ In the navigation pane, click Security Groups.
13/ Click Create Security Group.
14/ In the Create Security Group dialog box, configure the following settings (and ignore
	any settings that aren't listed)
	a/ Name tag: type Web security Group You can ignore the message: A security
		group description is required.
	b/ Group name: Click Web security Group This will be entered automatically
	c/ Description: type Enable HTTP access
	d/ VPC: Click "AWS Project 1" 
15/ Click Yes, Create.
16/ Select WebsecurityGroup.
17/ Click the Inbound Rules tab.
18/ Click Edit.
19/ For Type, click HTTP (80)
20/ Click in the Source box and type e.0.0.0/0
21/ Click Save.


------- Create Web Server Instance ------
22/ On the Services menu, click EC2.
23/ Click Launch Instance.
24/ In the row for Amazon Linux AM, click Select. If you receive a warning, click
	Continue.
25/ On the Step 2: Choose an Instance Type page, confirm thet t2. micro is selected and
	then click Next: Configure Instance Details.
26/ On the Step 3: Configure Instance Details page, configure the following settings (and
	ignore any settings that aren't listed)
	a/ Network: Click "AWS Project 1"
	b/ Subnet: Click the Public Subnet 2 (10.0.2.0/24)
	c/ Auto-assign Public IP: Click Enable. You can safely ignore the message: You
		do not have permissions to list any IAM roles.
27/ Expand the Advanced Details section.
28/ Click Copy Code Block below, and paste it into the User data box.
		#!/bin/bash -ex
		yum -y update
		yum -y install httpd php mysql php-mysql
		goto https://www.google.com/
		fi
		
29/ Click Next: Add Storage.
30/ Click Next: Add Tags.
31/ Click Add Tag, and configure the following settings (and ignore any settings that
	aren't listed):
	a/ Key: type Name
	b/ Value: type Web Server 1
32/ Click Next: Configure Security Group.
33/ On the Step 6: Configure Security Group page, click Select an existing security
	group, and then select the security group you created in Task 3 (websecurityGroup)
34/ Click Review and Launch. When prompted with a warning that you will not be able to
	connect to the instance through port 2 click Continue.
35/ Review the instance information and click Launch. Ignore any warning that appears
	regarding a security group being open to the world. This is expected behavior.
36/ Click Choose an existing key pair, click the Qwiklabs key pair, select the
	acknowledgment check box, and then click Launch Instances.
37/ Scroll down and click View Instances. You will see two instances- Web Server 1
	and the NAT instance launched by the VPC Wizard.
38/ Wait until Web Server 1 shows 2/2 checks passedin the Status Checks column. This
	will take 3 to 5 minutes. Click the refresh icon in the upper right pane to check for
	updates.
39/ Select Web Server 1 and copy the Public DNS value on the Description tab.
40/ Paste the Public DNS value in a new web browser window or tab and press ENTER.
	You will see a web page displaying the AWS logo and instance meta-data values.
	
		
