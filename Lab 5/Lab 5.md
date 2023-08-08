# Lab 5: Build Your DB Server and Interact With Your DB Using an App

**Version 4.6.6 (TESS2)**

This lab is designed to reinforce the concept of leveraging an AWS-managed database instance for solving relational database needs.

_**Amazon Relational Database Service**_ (Amazon RDS) makes it easy to set up, operate, and scale a relational database in the cloud. It provides cost-efficient and resizable capacity while managing time-consuming database administration tasks, which allows you to focus on your applications and business. Amazon RDS provides you with six familiar database engines to choose from: Amazon Aurora, Oracle, Microsoft SQL Server, PostgreSQL, MySQL and MariaDB.

**Objectives**

After completing this lab, you can:

- Launch an Amazon RDS DB instance with high availability.
- Configure the DB instance to permit connections from your web server.
- Open a web application and interact with your database.

**Duration**

This lab takes approximately **30 minutes**.

**Scenario**

You start with the following infrastructure:
![img](Pasted image 20230628115753.png)

At the end of the lab, this is the infrastructure:

![image](Pasted%20image%2020230628115827.png)

---

## Accessing the AWS Management Console

1. At the top of these instructions, choose Start Lab to launch your lab.
    
    A Start Lab panel opens displaying the lab status.
    
2. Wait until you see the message "**Lab status: ready**", then choose the **X** to close the Start Lab panel.
    
3. At the top of these instructions, choose AWS
    
    This will open the AWS Management Console in a new browser tab. The system will automatically log you in.
    
    **Tip**: If a new browser tab does not open, there will typically be a banner or icon at the top of your browser indicating that your browser is preventing the site from opening pop-up windows. Choose on the banner or icon and choose "Allow pop ups."
    
4. Arrange the AWS Management Console tab so that it displays along side these instructions. Ideally, you will be able to see both browser tabs at the same time, to make it easier to follow the lab steps.
    

---

## Task 1: Create a Security Group for the RDS DB Instance

In this task, you will create a security group to allow your web server to access your RDS DB instance. The security group will be used when you launch the database instance.

5. In the **AWS Management Console**, on the Services menu, choose **VPC**.
    
6. In the left navigation pane, choose **Security Groups**.
    
7. Choose Create security group and then configure:
    
    - **Security group name:** `DB Security Group`
    - **Description:** `Permit access from Web Security Group`
    - **VPC:** _Lab VPC_
    
    You will now add a rule to the security group to permit inbound database requests.
    
8. In the **Inbound rules** pane, choose Add rule
    
    The security group currently has no rules. You will add a rule to permit access from the _Web Security Group_.
    
9. Configure the following settings:
    
    - **Type:** _MySQL/Aurora (3306)_
    - **CIDR, IP, Security Group or Prefix List:** Type `sg` and then select _Web Security Group_.
    
    This configures the Database security group to permit inbound traffic on port 3306 from any EC2 instance that is associated with the _Web Security Group_.
    
10. Choose Create security group
    
    You will use this security group when launching the Amazon RDS database.
    

---

## Task 2: Create a DB Subnet Group

In this task, you will create a _DB subnet group_ that is used to tell RDS which subnets can be used for the database. Each DB subnet group requires subnets in at least two Availability Zones.

11. On the Services menu, choose **RDS**.
    
12. In the left navigation pane, choose **Subnet groups**.
    
    If the navigation pane is not visible, choose the menu icon in the top-left corner.
    
13. Choose Create DB Subnet Group then configure:
    
    - **Name:** `DB-Subnet-Group`
    - **Description:** `DB Subnet Group`
    - **VPC:** _Lab VPC_
14. Scroll down to the **Add Subnets** section.
    
15. Expand the list of values under **Availability Zones** and select the first two zones: **us-east-1a** and **us-east-1b**.
    
16. Expand the list of values under **Subnets** and select the subnets associated with the CIDR ranges **10.0.1.0/24** and **10.0.3.0/24**.
    
    These subnets should now be shown in the **Subnets selected** table.
    
17. Choose Create
    
    You will use this DB subnet group when creating the database in the next task.
    

---

## Task 3: Create an Amazon RDS DB Instance

In this task, you will configure and launch a Multi-AZ Amazon RDS for MySQL database instance.

Amazon RDS _**Multi-AZ**_ deployments provide enhanced availability and durability for Database (DB) instances, making them a natural fit for production database workloads. When you provision a Multi-AZ DB instance, Amazon RDS automatically creates a primary DB instance and synchronously replicates the data to a standby instance in a different Availability Zone (AZ).

18. In the left navigation pane, choose **Databases**.
    
19. Choose Create database
    
    If you see **Switch to the new database creation flow** at the top of the screen, please choose it.
    
20. Select **MySQL** under **Engine Options**.
    
21. Under **Templates** choose **Dev/Test**.
    
22. Under **Availability and durability** choose **Multi-AZ DB instance**.
    
23. Under **Settings**, configure:
    
    - **DB instance identifier:** `lab-db`
    - **Master username:** `main`
    - **Master password:** `lab-password`
    - **Confirm password:** `lab-password`
24. Under **DB instance class**, configure:
    
    - Select **Burstable classes (includes t classes)**.
    - Select _db.t3.micro_
25. Under **Storage**, configure:
    
    - **Storage type:** _General Purpose (SSD)_
    - **Allocated storage:** _20_
26. Under **Connectivity**, configure:
    
    - **Virtual Private Cloud (VPC):** _Lab VPC_
27. Under **Existing VPC security groups**, from the dropdown list:
    
    - Choose _DB Security Group_.
    - Deselect _default_.
28. Expand **Additional configuration**, then configure:
    
    - **Initial database name:** `lab`
    - Uncheck **Enable automatic backups**.
    - Uncheck **Enable encryption**
    - Uncheck **Enable Enhanced monitoring**.
    
    This will turn off backups, which is not normally recommended, but will make the database deploy faster for this lab.
    
29. Choose Create database
    
    Your database will now be launched.
    
    If you receive an error that mentions "not authorized to perform: iam:CreateRole", make sure you unchecked _Enable Enhanced monitoring_ in the previous step.
    
30. Choose **lab-db** (choose the link itself).
    
    You will now need to wait **approximately 4 minutes** for the database to be available. The deployment process is deploying a database in two different Availability zones.
    
    While you are waiting, you might want to review the [Amazon RDS FAQs](https://aws.amazon.com/rds/faqs/) or grab a cup of coffee.
    
31. Wait until **Info** changes to **Modifying** or **Available**.
    
32. Scroll down to the **Connectivity & security** section and copy the **Endpoint** field.
    
    It will look similar to: _lab-db.cggq8lhnxvnv.us-west-2.rds.amazonaws.com_
    
33. Paste the Endpoint value into a text editor. You will use it later in the lab.
    

---

## Task 4: Interact with Your Database

In this task, you will open a web application running on your web server and configure it to use the database.

32. To copy the **WebServer** IP address, choose on the Details drop down menu above these instructions, and then choose Show.
    
33. Open a new web browser tab, paste the _WebServer_ IP address and press Enter.
    
    The web application will be displayed, showing information about the EC2 instance.
    
34. Choose the **RDS** link at the top of the page.
    
    You will now configure the application to connect to your database.
    
35. Configure the following settings:
    
    - **Endpoint:** Paste the Endpoint you copied to a text editor earlier
    - **Database:** `lab`
    - **Username:** `main`
    - **Password:** `lab-password`
    - Choose **Submit**
    
    A message will appear explaining that the application is running a command to copy information to the database. After a few seconds the application will display an **Address Book**.
    
    The Address Book application is using the RDS database to store information.
    
36. Test the web application by adding, editing and removing contacts.
    
    The data is being persisted to the database and is automatically replicating to the second Availability Zone.
    

---

## Lab Complete

Congratulations! You have completed the lab.

37. Choose End Lab at the top of this page and then choose Yes to confirm that you want to end the lab.
    
    A panel will appear, indicating that "DELETE has been initiated... You may close this message box now."
    
38. Choose the **X** in the top right corner to close the panel.
    

_©2020 Amazon Web Services, Inc. and its affiliates. All rights reserved. This work may not be reproduced or redistributed, in whole or in part, without prior written permission from Amazon Web Services, Inc. Commercial copying, lending, or selling is prohibited._

---

### Attributions

**Bootstrap v3.3.5 - [http://getbootstrap.com](https://getbootstrap.com "http://getbootstrap.com")/**

The MIT License (MIT)

Copyright (c) 2011-2016 Twitter, Inc.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.