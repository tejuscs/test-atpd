<table class="tbl-heading"><tr><td class="td-logo">![](images/obe_tag.png)

June 13, 2019
</td>
<td class="td-banner">
# Lab 4: Provisioning databases on your dedicated Autonomous Infrastructure
</td></tr><table>

## Introduction

This lab walks you through the steps to get started using the Oracle Autonomous Transaction Processing Database on Oracle dedicated Autonomous Infrastructure. You will provision a new database.

To **log issues**, click [here](https://github.com/oracle/learning-library/issues/new) to go to the github oracle repository issue submission form.

## Objectives

As a database user, DBA or application developer,

- Rapidly deploy autonomous transaction processing databases
- Manage your database backups

## Required Artifacts

- To complete this lab you need access to an Oracle Cloud Infrastructure account with a pre-provisioned Exadata Infrastructure and Container Database


# Provisioning an Autonomous Transaction Processing Database Instance

In this section you will be provisioning a dedicated autonomous database using the cloud console.
## Steps

### **STEP 1: Sign in to Oracle Cloud Infrastructure console**

- Go to cloud.oracle.com, click Sign In to sign in with your Oracle Cloud account.

![](./images/400/signin.png)

- Enter your Cloud Account Name and click My Services.

![](./images/400/cloudaccname.png)

- Enter your Oracle Cloud username and password, and click Sign In.

![](./images/400/unpw.png)

- Once you are logged in, you are taken to the cloud services dashboard where you can see all the services available to you.

- Click Autonomous Transaction Processing in the left side menu under services

![](./images/400/myservices.png)


### **STEP 2: Create an ATP Instance**

-  Click on the hamburger menu icon on the top left of the screen

![](./images/400/Picture100-20.jpeg)

-  Click on **Autonomous Transaction Processing** from the menu

![](./images/400/Picture100-21.jpeg)

- Select **dbUserCompartment Compartment** 

![](./images/400/dbUserCompartment.png)

-  Click on **Create Autonomous Transaction Processing Database** button to start the instance creation process

![](./images/400/createATP-D.png)

-  This will bring up Create ATP Database screen where you specify the configurations of the instance

![](./images/400/provisionATP-D.png)


#### Note: Oracle Cloud Infrastructure allows logical isolation of users within a tenant through Compartments. This allows multiple users and business units to share a tenant account while being isolated from each other.

If you have chosen the compartment you do not have privileges on, you will not be able to see or provision instance in it.

More information about Compartments and Policies is provided in the OCI Identity and Access Management documentation [here](https://docs.cloud.oracle.com/iaas/Content/Identity/Tasks/managingcompartments.htm?tocpath=Services%7CIAM%7C_____13).

-  Verify dbUserCompartment compartment is selected and Specify a name for the instance

![](./images/400/provisionATP-Dname.png)

-  Choose workload type to Transaction Processing and deployment type to Dedicated Infrastructure

![](./images/400/provisionATP-Dworkloads.png)


-  You can choose an instance shape, specified by the CPU count and storage size. Default CPU count is 1 and storage is 1 TB.

![](./images/400/provisionATP-DCPU.png)

-  Specify the password for the instance

#### For this lab, we will be using the following as password

```
WElcome#1234
```

![](./images/400/Picture100-29.jpeg)

- Make sure you have already created Autonomous Container Database
- Choose Autonomous Container Database

![](./images/400/provisionATP-Dcontainer.png)


- Make sure you have everything filled all required details

-  Click on **Create Autonomous Transaction Processing Database** to start provisioning the instance

![](./images/400/Picture100-31.jpeg)

- Once you create ATP Database it would take 2-3 minutes for the instance to be provisioned.

![](./images/400/waitprovision.png)

-  Once it finishes provisioning, you can click on the instance name to see details of it

![](./images/400/doneprovision.png)

You now have created your dedicated Autonomous Transaction Processing database.



<table>
<tr><td class="td-logo">[![](images/obe_tag.png)](#)</td>
<td class="td-banner">

</td>
</tr>
<table>