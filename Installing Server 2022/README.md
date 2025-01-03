# Installing Windows server in virtualbox

In this guide, we’ll walk you through the steps to install Windows Server 2022 in VirtualBox. First, make sure to download the Windows Server 2022 ISO file from the official Microsoft website.

>Download ISO:  https://info.microsoft.com/ww-landing-windows-server-2022.html

![initial](img/vm-initializing%201.png)

To ensure smooth performance, allocate at least 4GB of RAM and 2 CPU cores to the virtual machine during setup. This configuration will provide a stable environment for running Windows Server 2022.

![ram&cpu 1.png](img/ram&cpu%201.png)

If you encounter an error during the virtual machine's setup or installation startup, don’t worry. Simply shut down the virtual machine and follow these steps to resolve the issue.

![os-installation-error 1.png](img/os-installation-error%201.png)

Navigate to Settings Menu -> Storage -> Under Controller: SATA:
1. Remove the floppy disk
 2. check the Live CD\DVD

![vm-settings 1.png](img/vm-settings%201.png)

After completing the necessary adjustments, restart the virtual machine to proceed with the installation process.

![installation-success 1.png](img/installation-success%201.png)

When prompted during the installation process, select the second option, "Desktop Experience," to install the GUI version of Windows Server 2022. This option provides a graphical user interface for easier management and navigation.

![GUI Install 1.png](img/GUI%20Install%201.png)

To enter login credentials. First press the following button, which is `Ctrl+Alt+Delete` to unlock.

![input.png](img/input.png)

> NOTE: If you have MAC OS and want to test Active Directory. Check this blog on how you can achieve https://medium.com/@tech-n0/ad-lab-on-m1-for-oscp-915e42be74f3

Congratulations! You have successfully installed Windows Server 2022 on VirtualBox. Your virtual machine is now ready for use, whether for testing, learning, or deploying server applications. 
