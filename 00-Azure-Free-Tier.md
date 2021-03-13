# Day 0 - Creating Your Own Server - with Azure Free Credits

* [Previous "Day 0" threads](https://www.reddit.com/r/linuxupskillchallenge/search/?q=Day%200&restrict_sr=1)

## INTRO

First, you need a server. You can't really learn about administering a remote Linux server without having a one of your own - so today we're going get one - completely free!

Through the magic of Linux and virtualisation, it's now possible to get a small Internet server setup almost instantly - and at very low cost. Technically, what you'll be doing is creating and renting a VPS  ("Virtual Private Server"). In a datacentre somewhere a single physical server running Linux will be split into a dozen or more Virtual servers using the KVM (Kernel-based Virtual Machine) feature that's been part of Linux since early 2007.

As well as a hosting provider, we also need to choose which "flavour" of Linux to install on our server. If you're new to Linux then the range of "distributions" available can be confusing - but the latest LTS ("Long Term Support") version of Ubuntu Server is a popular choice, and what you'll need for this course.

These instructions will walk you through using Azure's free credits.

## Signing up with Azure

Sign-up is fairly simple - just provide your email address and a password of your choosing - along with a phone number for a 2FA - a second method of authentication. Azure can be a bit funny about 'corporate' email addresses, eg using a work address or your own domain. Create a new @outlook or @gmail.com account if so using the link on the sign-up page.

You will need to also provide your VISA or other credit card information.

### Create your first resource group, virtual network, and virtual machine

From the Home screen in the Azure Portal choose "Create a Resource"

* Enter "Resource group" in the search box
* Choose Create
* Enter a region and name then choose "Create"
* Go back to Home and choose "Create a resource"
* Search for virtual network
* Choose Create
* Choose the resource group you just made as the location for this virtual network
* Enter a name for your vnet like ("vnet-sbonds-linuxupskillchallenge")
* Choose Review + Create
* Review
* Create
* When your deployment is complete, go back to the Azure Portal Home
* Choose "Create a resource"
* Choose the Ubuntu Server 18.04 LTS from the popular list
  * If you search be sure the image is free and provided by "Canonical" as the publisher
  * Avoid images with text like "Software plan starts at $X.XX per hour"
  * Ubuntu 20 is not available on Azure except as an extra-charge "Pro" version
* Choose Create
* Change the resource group to the one you created earlier
* Change the size to Standard_B1ms (unless there's another option for you which is free)
* Keep the default authentication type of "SSH Public key"
* Use the default user "azureuser"
* Keep the default "generate new key pair"

* Ensure 'SSH Public Key' for authentication and 'generate new key pair' for SSH Public Key source are selected
* Leave 'allow selected ports' as 'ssh (22)' for now
* Click 'Review + Create'
* Azure will generate and download the private key file to SSH onto the box. This is in the unusual PEM format.
* Choose Go to Resource
* Note the public IP

### Log in with Windows/PuTTY

* In PuTTYGen open the PEM file downloaded via "Conversions - Import Key"
* Set a strong pass phrase
* Set a descriptive key comment
* Save public key
* Save private key

* Open PuTTY itself
* Put the public IP of your new VM in the "Host Name (or IP address)" field
* In the menu along the left expand the SSH category in PuTTY by clicking the "+"
* Click on "Auth" (not the "+" this time)
* Near "Private key file for authentication" choose "Browse" and browse to your private key file
* (optional) In Connection - Data, put "azureuser" in the auto-login username
* (optional) In Session (top) Under Saved Sessions give it a name and save the session
* Answer "yes" to the "The server's host key is not cached" prompt

Now to fully expose the machine and all ports to the internet:

* Navigate to [the Azure Portal](https://portal.azure.com/#home)
* Select 'Virtual Machines'
* Select your created virtual machine and select 'Networking' from the settings pane
* Click 'Inbound Port Rules' and 'Add inbound port rule'
* Set 'source port ranges' and 'destination port ranges' to '*' and set 'Source' and 'Destination' to 'any'. Ensure protocol is set to 'any' and action is set to 'allow'. Set the priority to '100' and create an appropriate name

This opens all ports and protocols to access from anywhere. While this might be unwise for a production server, it is what we want for this course so we can later see what a big mess it is on the Internet.

## Remote access via SSH

Ensure your machine is 'running' (if not, click 'start') and connect using the 'connect -> ssh' dropdown and following instructions

You will be logging in as the user *azureuser*. It has been added to the 'adm' and 'sudo' groups, which on an Ubuntu system gives it access to read various logs - and to "become root" as required via the _sudo_ command.

## You are now a sysadmin

Confirm that you can do administrative tasks by typing:

`sudo apt update`

(Normally you'd expect this would prompt you to confirm your password, but because you're using public key authentication the system hasn't prompted you to set up a password - and Azure have configured *sudo* to not request one for "azureuser").

Then:

`sudo apt upgrade`

Don't worry too much about the output and messages from these commands, but it should be clear whether they succeeded or not. (Reply to any prompts by taking the default option). These commands are how you force the installation of updates on an Ubuntu Linux system, and only an administrator can do them.

To logout, type _logout_ or _exit_ or (for the very lazy) `<ctrl>-d`

Your server is now all set up and ready for the course!

Note that:

* This server is now running, and completely exposed to the whole of the Internet
* You alone are responsible for managing it
* You have just installed the latest updates, so it should be secure for now

## Additional nicities for overachievers

### Use "pageant" for holding your SSH key

This way you don't need to enter the key pass phrase each time you log in.

### Set up a DNS name for your VM

Then you can configure PuTTY with the name instead of the IP, which will persist even when shut down.

#### Use your DNS name in PuTTY

Create a session named after your host.

### Change your SSH key to one you can use lots of places

Use Azure's "Reset Password" feature to change the SSH key to an OpenSSH format key created via PuTTYGen.

### Create a storage account to store your VM's serial port logs

And enable serial port logging and access. This is a nice feature found on Azure as only a more limited version of this exists in AWS.
