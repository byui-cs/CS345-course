![](../images/banner.jpg)

# Setup -Terminal

Connecting to the Linux Lab is perhaps easiest on a Macintosh computer because no tools need to be installed. Everything you need is built right into the OS-X platfrom with the Terminal program. To get this to work on your Macintosh, please follow these steps:

1.  Go to your Applications folder, then scroll down to Utilities. There you will find an Application called "Terminal". Double-click to launch that application. (You may want to drag this icon to your dock at the bottom of the screen to make launching a terminal easier in the future.)

    ![The X11 Application](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/Terminal-1-term.png "The X11 Application")
2.  Once this appication is running, if you don't see a window, press ⌘-N (Command-N) to open a new Terminal window. Once the window is open, type the following SSH command to connect to the linux lab.

    Make sure you replace "yourname" with your username and "the.computer.ip.address" with the I.P. address you copied down from the lab earlier. Note that we're using a **capital X** and a **lowercase p** in this command.

    <div class="code">`ssh -X yourname@the.computer.ip.address -p 215`</div>

    The host name (IP address) needs to `157.201.194.xxx` where the “`xxx`” is replaced by one of the values `201` to `210`. For example: `157.201.194.207` Once you pick one of the 10 machines to use, you will probably always use that system. If at some point, you are having problems getting a connection to the Linux Lab, you might change your configuration to use a different system (`157.201.194.201` through `157.201.194.210`) to see if the entire lab is down, or if just the system you are trying to use is down. For example, if I choose `157.201.194.210` and my netID was `code4ever`, then I would type:

    <div class="code">`ssh -X code4ever@157.201.194.210 -p 215`</div>

    ![The Terminal with the SSH command entered.](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/Terminal-2-term.png "The Terminal with the SSH command entered.")
3.  Press Enter to connect to execute the command. The first time you do this you will be asked if you want to trust the machine. Type _yes_ and press enter. Once you type your password and press enter again, you will be connected to the lab.

    ![The X11 Terminal connected to the Linux Lab.](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/Terminal-3-connected.png "The X11 Terminal connected to the Linux Lab.")
4.  You can now open an emacs window by typing _emacs_ and pressing enter. If everything is working properly, an emacs window will appear on your desktop. You can interact with this window using your mouse and keyboard, just as you do in the lab.

    ![The emacs window.](https://content.byui.edu/items/cce78209-6169-4309-9e80-7c57febd4d75/1/Terminal-3-emacs.png "The emacs window.")

There are several other tools available to Macintosh users:

*   SSH: [Using the terminal shell](https://video.byui.edu/media/SSH/0_fg803qeq/21931002)
*   textWrangler: [Installing](https://video.byui.edu/media/TextWrangler-Install/0_2ekga5ed/21931002), [configuring](https://video.byui.edu/media/textWrangler-Config/0_u9ig228b/21931002), and [tips](https://video.byui.edu/media/textWrangler-Tips/0_gzu1n4ot/21931002)
*   Xcode: [Downloading](https://video.byui.edu/media/xCode-Download/0_9mxcigsv/21931002), [adding files](https://video.byui.edu/media/xCode-AddingFiles/0_4tley8in/21931002), and [setting up](https://video.byui.edu/media/xCode-Setup/0_rq8hpxtu/21931002). There is also the following tutorial for using X-Code: [Xcode setup for Macintosh computer](https://content.byui.edu/file/cce78209-6169-4309-9e80-7c57febd4d75/1/IDE%20-%20Xcode%20Setup.pdf)
*   cyberDuck: [Coping files to your hard disk](https://video.byui.edu/media/cyberDuck/0_6zolgzzf/21931002).

