## Installing Python, pip, and virtualenv

If you are on a Mac running OSX (10.7+), you have a couple options for setting up your environment.

The first is to use the __system Python__--the Python that comes pre-installed on your Mac. This has the advantage of being easy--no install required!--but has the disadvantage of being a) heavily modified by Apple, b) likely out-of-date.

The second option is to install the package manager __Homebrew__ to install Python and manage downloads. This is generally advisable because Mac system updates have been known to nuke overwrite downloads, forcing a reinstall of any lost packages. Homebrew also handles all the symlinking for you (meaning that it will tell your system how to find any packages you install) and makes upgrading your working version of Python easy.

 If you’d like to learn more about Homebrew and it’s possible advantages, this [article](http://computers.tutsplus.com/tutorials/homebrew-demystified-os-xs-ultimate-package-manager--mac-44884) is great and also explains packages and package managers more generally.

 *It is not necessary to use Homebrew, and you shouldn't worry if you've already installed pip and virtualenv on top of your system Python.*


###Install the latest version of XCode and XCode’s Command Line Tools
_Note: Mountain Lion and above: You can skip XCode and go straight for the Command Line Tools_

Locate the XCode icon in Launchpad or in Finder/Applications, and double-click. From the menubar, click XCode/Preferences and then select "Downloads". Choose the command line tools option, if presented (if it isn't, you probably already installed them.)


###System Python users:
_Note: all commands are prefaced with a ‘$’ and should be entered into the command line in your Terminal app (or iTerm, if you prefer). Don’t type the ‘$’--this is the symbol for your prompt_

First we'll install the Python-specific package manager, ‘pip’, and then we'll use pip to install virtualenv.

````
$ sudo easy_install pip
$ pip install virtualenv
````

To verify that our downloads worked, run the following:

````
$ which virtualenv
$ which pip
//  If you got results for each of these, your installs worked
````


###Homebrew users:
_Note: all commands are prefaced with a ‘$’ and should be entered into the command line in your Terminal app (or iTerm, if you prefer). Don’t type the ‘$’--this is the symbol for your prompt_

Install Homebrew using the install script listed [here](http://brew.sh/) (near the bottom of the page). Then, run:

````$ brew doctor````

Follow any instructions that print out in your Terminal. This command will expose any issues that might be present on your system that could prevent a smooth install process.

Next, you’ll want to install Homebrew’s version of Python. This won’t overwrite your system Python; rather it will install Python (and pip, which is bundled) in another directory on your hard drive.

First, we need to tell homebrew where in your PATH to install Python, then we’ll install:

````
$ export PATH=/usr/local/bin:/usr/local/share/python:$PATH
$ brew install python --universal --with-brewed-openssl
````

* the universal says build 32/64 bit universal
* with-brewed-openssl updates the outdated version of the open ssl protocol that comes on Mavericks OSX 10.9
* optional: add the --framework option after --with-brewed-ssl, which lets you do a framework-style build versus a Unix-style build. If you use this, you’ll need to run these commands afterwards to create the proper symlink to point to this install:

````
$ cd /System/Library/Frameworks/Python.framework/Versions
$ sudo rm Current
$ ln -s /usr/local/Cellar/python/2.x.x/Frameworks/Python.framework/Versions/Current
````

Now, let's verify that our install worked by entering the following:

````
$ which python   // if you see /usr/local/bin/python, it worked
$ which pip   // if you see /usr/local/bin/pip, it worked
````

Finally, we'll need to install __virtualenv__:

````
$ pip install virtualenv
$ which virtualenv   // if you see /usr/local/bin/virtualenv, it worked
````

#### Sources:
[http://hackercodex.com/guide/python-development-environment-on-mac-osx/](http://hackercodex.com/guide/python-development-environment-on-mac-osx/)
[http://www.tlswebsolutions.com/mac-os-x-lion-setting-up-django-pip-virtualenv-and-homebrew/](http://www.tlswebsolutions.com/mac-os-x-lion-setting-up-django-pip-virtualenv-and-homebrew/)
[http://www.thisisthegreenroom.com/2011/installing-python-numpy-scipy-matplotlib-and-ipython-on-lion/](http://www.thisisthegreenroom.com/2011/installing-python-numpy-scipy-matplotlib-and-ipython-on-lion/)
[http://docs.python-guide.org/en/latest/starting/install/osx/#install-osx](http://docs.python-guide.org/en/latest/starting/install/osx/#install-osx)
[http://www.virtualenv.org/en/latest/virtualenv.html](http://www.virtualenv.org/en/latest/virtualenv.html)
[http://www.pip-installer.org/en/latest/installing.html](http://www.pip-installer.org/en/latest/installing.html)

