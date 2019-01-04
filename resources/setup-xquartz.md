![](../images/banner.jpg)

# Setup - XQuartz

XQuartz is a shell that runs on OS X enabling you to develop on a Macintosh computer in a similar way to how you would develop on a Linux computer. This is accomplished by providing a user interface (a "shell") build on the same X Window System that Linux is built on. Note that XQuartz was developed by Apple and, as such, is a supported development platform.

Once you have installed XQuartz on your computer, you can use emacs in a separate window much like you can on a native Linux computer. You can also run OpenGL applications such as the ones we develop in CS 165.

## Setup

In order to get up-and-running with XQuartz, you will need to install the XQuartz application. The following instructions explain how to install the necessary tools to remotely access GUI applications running on Linux Lab computers from a system running Apple Macintosh OS X. Of course, this document does not cover how to install the tools on Microsoft Windows computers.

### 1. Download

Download XQuartz dmg package on the web site [http://www.xquartz.org/](http://www.xquartz.org/)

![XQuartz web site](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/XQuartz-1-Download.png)

Figure 1 - XQuartz web site

### 2\. Start installation

Double click the downloaded file to start the installation process. You should see the screen below (See figure 2). Just click "Continue."

![Beginning installation](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/XQuartz-2-Install.png)

Figure 2 - Beginning installation

### 3\. Readme

The next scheme describes any notifications about this release. Click "Continue."

![Important information](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/XQuartz-3-Readme.png)

Figure 3 - Important information

### 4\. EULA

For the license agreement, click "Continue" (See figure 4) and on the pop up you must choose "Agree" (See figure 5) otherwise the installation will be canceled

![License agreement](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/XQuartz-4-EULA.png)

Figure 4 - License agreement

![Pop up asking for your agreement](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/XQuartz-4-Confirm.png)

Figure 5 - Pop up asking for your agreement

### 5\. Installation Type

The next screen will show you how much space you need to complete the installation. It takes 185.9 MB of space on your computer. Click "Install" to continue. (See figure 6)

![Space requirements](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/XQuartz-5-InstallType.png)

Figure 6 - Space requirements

### 6\. Installation

You will need to provide your Mac username and password in order to continue the installation process. (See figure 7)

![Mac username and password required](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/XQuartz-6-Password.png)

Figure 7 - Mac username and password required

This step of the process can take a few minutes. Even though seems stuck, just wait until the progress bar is full. (See figure 6)

![Wait until the progress bar is complete](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/XQuartz-7-Scripts.png)

Figure 8 - Wait until the progress bar is complete

You should see the message after the progress bar is complete. It is just an informative message telling you to log out and log back in to use the application. (See figure 9)

![Informative Message](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/XQuartz-7-Progress.png)

Figure 9 - Informative Message

Finally, you will see the message saying "The installation was successful." The installation is now complete. (See figure 10)

![Installation Complete](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/XQuartz-7-Success.png)

Figure 10 - Installation Complete

## Running XQuarts

In order to test the new application, first log out and log back in. Then open the terminal window and type the following command where `2xx` may be `201` through `210` and "`yourusername`" is replaced by the username you use to log in to the Linux Lab computers

<div class="code">`ssh –X –p 215 yourusername@157.201.194.2xx`</div>

![Terminal command](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/XQuartz-10-Terminal.png)

Figure 11 - Terminal command

The first time you access Linux Lab through this process you should see a message like the one below (See figure 12). This is normal. It is just saying the file `.Xauthority` used to graphical remote access does not exist, but Linux will create one for you. The next time this message won't appear anymore.

![File does not exist](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/XQuartz-11-Terminal.png)

Figure 12 - File does not exist

When you see your username followed by "`@`" and the hostname of the machine (`ausXXXX`) as pointed by the arrow below, you know you are already inside the Linux Lab terminal. Type "`gedit`" to open the GUI text editor to test it. You should see the graphical text editor as shown below. (See figure 13)

![gedit GUI](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/XQuartz-12-GEdit.png)

Figure 13 - gedit GUI

Now you can use the Linux Lab GUI applications remotely on your Macintosh.

