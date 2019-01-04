![](../images/banner.jpg)

# Setup - Moba XTerm

There are several programs available for Windows which will allow you to connect to the Linux Lab. These instructions will show you how to install [MobaXTerm](http://mobaxterm.mobatek.net/).

1.  Go to the [MobaXTerm website](http://mobaxterm.mobatek.net/) and click the Get MobaXTerm Now button, or click the Download menu item at the top of the screen.

    ![Mobaxterm Website](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/Moba-1-download.png?.vi=fancy "Mobaxterm Website")

    Once on the download page, choose the free edition, then click the button for the Installer Edition.

    ![Mobaxterm Free Edition](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/Moba-1-free.png?.vi=fancy "Mobaxterm Free Edition")

    ![Mobaxterm Installer](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/Moba-1-installer.png?.vi=fancy "Mobaxterm Installer")

2.  Once the installer has donwloaded, double-click the installer file to install the program to your computer. If a security warning appears, select the option to "Run" or "Proceed", then follow the instructions on the screen to finish the installation.

    Once the installation completes, you should see an icon on your desktop labeled 'MobaXterm Personal Edition'.

    ![Mobaxterm Icon](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/Moba-2-icon.png?.vi=fancy "Mobaxterm Icon")

3.  Double-click the icon to run Mobaxterm. In the window that appears, click the "Session" button in the upper left hand corner to create a new session.

    ![Mobaxterm New Session Icon](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/Moba-3-session.png?.vi=fancy "Mobaxterm New Session Icon")

    In the window that appears, click the SSH button at the top of the screen to create a new SSH session. Enter the IP address of the Linux Lab machine you would like to connect to. The host name (IP address) needs to `157.201.194.xxx` where the “`xxx`” is replaced by one of the values `201` to `210`. For example: `157.201.194.207` Once you pick one of the 10 machines to use, you will probably always use that system. If at some point, you are having problems getting a connection to the Linux Lab, you might change your configuration to use a different system (`157.201.194.201` through `157.201.194.210`) to see if the entire lab is down, or if just the system you are trying to use is down.

    Check the "Specify username" box and enter your username. Change the port from 22 to 215\. Once everything looks right, click the OK button.

    ![Mobaxterm Session Config](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/Moba-3-settings.png?.vi=fancyg "Mobaxterm Session Config")

4.  Mobaxterm will now attempt to connect to the Linux Lab and will then prompt you for your password. Once you enter your password and press enter, it will ask if you want to save your password. While this can save you time, it may not be the most secure thing to do.

    Once you've entered your password successfully, you will be connected to the Linux Lab.

    ![Mobaxterm Terminal Window](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/Moba-4-connected.png "Mobaxterm Terminal Window")

    On the right side of the screen is a terminal window where you can enter commands as if you were in the Linux Lab.

    On the left side of the screen is an SFTP file browser, which will allow you to drag and drop files between your Windows PC and your Linux Lab account.

5.  You can now run emacs just as you would in the Linux Lab by clicking in the right-hand terminal window and typing `emacs`.

    If everything is working properly, an emacs window will appear on your desktop. You can interact with this window using your mouse and keyboard, just as you do in the lab.

    ![Mobaxterm Emacs Window](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/Moba-5-emacs.png "Mobaxterm Emacs Window")

6.  The next time you launch Mobaxterm, the session configuration you entered in step 3 will be shown on the left side of the screen. Simply double-click the session to open a connection to the Linux Lab.

    ![Mobaxterm Saved Session](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/Moba-6-saved.png "Mobaxterm Saved Session")
