<table class="tbl-heading"><tr><td class="td-logo">![](images/obe_tag.png)

June 13, 2019
</td>
<td class="td-banner">
# Lab 7: Building and deploying Python application stacks on dedicated autonomous infrastructure
</td></tr><table>

To **log issues**, click [here](https://github.com/oracle/learning-library/issues/new) to go to the github oracle repository issue submission form.

## Introduction
The Oracle Cloud Infrastructure marketplace provides a pre-built image with necessary client tools and drivers to build applications on autonomous databases. As an application developer you can now provision a developer image within minutes and connect it to your dedicated or serverless database deployment. 

The image is pre-configured with tools and language drivers to help you build applications written in node.js, python, java and golang.
For a complete list of features, login to your OCI account, select 'Marketplace' from the top left menu and browse details on the 'Oracle Developer Cloud Image'


## Objectives

As an application developer,
- Learn how to deploy a python application and connect it to your dedicated autonomous database instance

## Required Artifacts

-  Access to an Oracle Cloud Infrastructure account

- A pre-provisioned instance of Oracle Cloud Developer Image from the OCI marketplace

- A pre-provisioned instance of dedicated autonomous database

## Steps

### **STEP 1: SSH into Oracle Cloud Developer image and clone Python application**

- Login to your Oracle Cloud Infrastructure account and click on **Menu** and select **Compute** and **Instances**

![](./images/800/Compute1.png)

- Select the right Oracle Developer Cloud image you created in earlier labs. 

- Copy the public IP address of the instance in a note pad. 

![](./images/800/Compute2.png)


### For Mac users

- Open Terminal and SSH into linux host machine

```
sudo ssh -i /path_to/sshkeys/id_rsa opc@publicIP
```

![](./images/800/SSH1.png)

### For Windows users

- You can connect to and manage linux host mahine using SSH client. Recent versions of Windows 10 provide OpenSSH client commands to create and manage SSH keys and make SSH connections from a command prompt.

- Other common Windows SSH clients you can install locally is PuTTY. Click [here](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/ssh-from-windows) to follow the steps to connect to linux host machine from you windows using PuTTY.

### Cloning Python Application

- Download a sample Python application [here ](/./scripts/700/ATPDpython-master.zip) and scp it to your development host in folder /home/opc

```
$ scp /path/to/your/ATPDpython-master.zip -i <priv-key> opc@<IPAddress>:/home/opc/
```

- ssh back into your host and unzip ATPDpython-master.zip

```
$ unzip /home/opc/ATPDpython-master.zip
```
Now that you have a sample application setup, lets get your database's secure wallet for connectivity

### **STEP 2: Secure Copy ATP Dedicated database wallet to linux host machine**

- Login to Oracle Cloud Infrastructure account and click on **Menu** and **Autonomous Transaction Processing**
![](./images/800/atpd1.png)

- Click on Autonomous Database and select your previously created database

![](./images/800/atpd2.png)

- Click on DB Connection and under Download Client Credential(Wallet) click **Download**

![](./images/800/atpd3.png)

- Database connections to you Autonomous Database use a secure connection. You will be asked to create a password for yopu wallet. 

- Enter **Password** and **Confirm password** and click on **Download**

![](./images/800/atpd4.png)

- The credentials zip file contains the encryption wallet, Java keystore and other relevant files to make a secure TLS 1.2 connection to your database from client applications. Store this file in a secure location.

- Let us now secure copy the downloaded wallet to our linux host machine

- Open Terminal in your laptop and type in the following commands

#### Note: Please change the path for both private ssh key and wallet in below command

```
sudo scp -i /Path/to/your/private_ssh_key /Path/to/your/downloaded_wallet opc@publicIP:/home/opc/
```
![](./images/800/atpd5.png)

- You are now ready to move to step 3

### **STEP 3: Confuigure env variables and run python application in linux host machine**

Now that you have copied the database wallet to your development host, lets configure some env. variables and database authentication file to connect your Python app to the database

- On your dev host, create a new directory for wallet and unzip the wallet

```
cd /home/opc/ATPDpython/

mkdir wallet

unzip Wallet_ATPDedicatedDB.zip -d /home/opc/ATPDpython/wallet/
```
- The sqlnet.ora file in your wallet folder needs to have an entry pointing to the location of the wallet folder. Open the file in vi editor as follows,

```
vi /home/opc/ATPDpython/wallet/sqlnet.ora
```

- Change **DIRECTORY** path to /home/opc/ATPDpython/wallet/ and save the file

![](./images/700/walletPython.png)

- Next, we also set up an environment variable TNS_ADMIN to point to the wallet location

```
export TNS_ADMIN=/home/opc/ATPDpython/wallet/
```

- Verify TNS_ADMIN path

```
echo $TNS_ADMIN
```
![](./images/700/TNSadmin.png)

- Run the python application

- Password for user 'admin' was set at the time of database creation
- Connectsring for your database is available on the cloud console. Check previous connectivity labs

```
 python exampleConnection.py ADMIN PASSWORD dbname_tp
```
![](./images/700/pythonSuccess.png)


- Congratulations! You successfully deployed and connected a Python app to your autonomous database.

<table>
<tr><td class="td-logo">[![](images/obe_tag.png)](#)</td>
<td class="td-banner">

</td>
</tr>
<table>