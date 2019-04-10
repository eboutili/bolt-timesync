In this lab you will complete the installation of the open source Bolt utility. Depending on the platform you wish to use (Windows or Linux), the process will look slightly different. Instructions are provided for both.

After completing this exercise you will have done the following:

* Installed the Bolt executable
* Executed a simple command to validate the utility is working

## Required resources
These are the resources required to complete this lab:

* A host machine to install the software.
* Install this utility on one of the classroom nodes you have been provided (Windows or Linux)

Task 1: Install Bolt
====================

## Lab procedure

Decide where you will install Bolt. You have the choice of installing Bolt onto a classroom provided Windows or Linux machine. If time allows, you can install Bolt onto multiple platforms. Once you've decided where you'll be installing Bolt, connect to the target machine (SSH or RDP depending) and follow the steps for your platform.

* [Windows](#windows)
* [Linux](#linux)

~~~PAGEBREAK~~~

## Windows

### Connect to the agent

.callout.info Remember, you can get the details of which student machines you should be using in the welcome page, located at https://class__XXXX__.classroom.puppet.com

1. Start the RDP client to connect to your agent
    * Windows:
        * Remote Desktop Connection
    * Mac OSX
        * Microsoft Remote Desktop 8 or 10
1. Connect with the following information
    * hostname: __XXXX__win__Y__.classroom.puppet.com
        * Remember, the hostname of your Windows machine can be retrieved from the class welcome page
    * username: Administrator
    * Password: `password from the welcome page`

### Step 1

Start a web browser on the server, and enter the URL to download the Puppet **MSI** installation file from: `https://downloads.puppet.com/windows/puppet5/puppet-bolt-x64-latest.msi`

Choose the Downloads folder as the save location.

### Step 2

When prompted by the browser, click **Run**. Follow the installation Wizard instructions. No customization is required, just **Accept the license**, click **Next** through the option windows, and click **Install**, and finally **Finish**.

### Step 3

Next, you'll validate the installation is working. Open a new PowerShell prompt and run: `bolt --version`

**Expected Output**

    @@@ Console nochrome
    PS C:\Users\Administrator> bolt --version
    0.21.3

.callout.info Your version will likely vary, and this is not a problem.

~~~PAGEBREAK~~~

## Linux

.callout.info The steps below detail connecting to your Linux machine from your student Windows machine (used above). If you would rather connect directly from your own laptop you can, however you will have to translate these instructions to the utilities you are using. The private key for the Linux machine can be downloaded from the Welcome page.

.callout.info There are many distributions of Linux. This classroom environment uses CentOS, however Bolt supports many different versions. See the official documentation for more details. The guide below is for CentOS 7.

For this lab you'll be leveraging the built-in package manager to install Bolt.

### Connecting to the Linux Host using PuTTY or Openssh method

#### PuTTY Method
1. On your Windows student machine, open a PowerShell window
1. Launch PuTTY by typing `putty` and pressing enter:
    * In the Host Name field, copy and paste your Linux machine's hostname from the Welcome page
    * On the left hand menu, expand `SSH` and click on **Auth**
        * Under `Private key file for authentication`, click the **Browse** button
        * Select the pre-loaded private key from `C:\keys`.
        * Select **private_key.ppk** and click **Open**
    * Next, under the `Connection` category, click on **Data**
        * In the `Auto-login username` field, type **centos**
    * Return to the session view by clicking **Session** on the left-hand menu in PuTTY
    * In the `Saved Sessions` box, type in **linux_machine** and click **Save** on the right hand side
    * Click **Open**
        * If prompted about the host key not being cached, select **Yes**

.callout.info For any future connections to this host, you can now simply double-click **linux_machine** in the `Saved Sessions` window

#### OpenSSH method

1. On your Windows student machine, open a PowerShell window
1. Install win32-openssh using chocolatey, `choco install openssh` and press enter:
    * When the install is done, restart PowerShell
    * You can then use the credentials already on the host
1. Re-open PowerShell and type in `ssh centos@<your-linux-machine>.classroom.puppet.com`

~~~PAGEBREAK~~~

### Step 1

Execute the following commands to add the required YUM repository and install the bolt package:

    @@@ Console nochrome
    sudo rpm -Uvh https://yum.puppet.com/puppet5/puppet5-release-el-7.noarch.rpm
    sudo yum install -y puppet-bolt

### Step 2

Now you will validate if your installation is working properly:

    @@@ Console nochrome
    $ bolt --version
    0.21.3

.callout.info Your version will likely vary, and this is not a problem.
