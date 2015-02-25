## Command Line I Recap

The goal of the Command Line I & II workshops is to get our environments set up for development and to begin to learn the basic tools that professional developers use everyday. In the case of Python, that means getting comfortable working in our shell environments and with the command-line interface (CLI).

Why the command line?

* It’s faster to navigate your file system vs using the Finder;

* There are tools and programs available for the command-line (like pip and virtualenv!) that don’t have GUI (graphical user interface) equivalents;

* Many people find that they’re able to understand the basics of their operating systems, as well as certain programs like git, better by interfacing with them via the command line;

* Knowing your way around the command line is a resume booster and you’ll impress all your friends and relatives!!


### Key definitions:

* __shell__ -- A shell is an interpreter that allows you to communicate with your computer’s operating system. There are many different flavors of shell for Unix and Unix-like systems, including bash, zsh, tsh. Bash is the default and most widely used. Windows users also have choices, most notably between the Command Prompt and Powershell. You may write scripts to customize your shell environment (more about this in Command Line II).


* __command-line interface__ -- The CLI is a feature of every shell environment, and allows you to enter and send Unix (Mac, Linux) or DOS (Windows) commands.


### Anatomy of a Command:

A typical command is made up of 2-4 parts:

* the __prompt__, symbolized by the ‘$’ symbol (Mac), and either ‘C:’ or ‘$’ symbols’ (Windows, depending on the shell you’re using. See [here](http://blog.simplyadvanced.net/cheat-sheet-for-windows-command-prompt/) for more info on Windows commands)

* the __command__, which is usually either a word or abbreviation that invokes a small program

* (optional) __option__ --also called flag, argument, or parameter--which modifies the command or program

* (optional) __filename, directory, extension__ --something we’re acting on


So, the structure to remember is:

````
$ command --argument
// or,
$ command --argument maybe_something_else
// if you're acting on a file, etc.
````


##### Quitting out in the command line: because it's good to have an out

* Ctrl-C (stops running processes)

* quit (as we’ll learn later, exit git tools and other small programs)

* exit() (Python and Django shells)



#### First Exercises

Now that we have the basic format down, let’s try a few. First, open your Terminal application and enter:

````
$ whoami   // just in case you forgot, prints your username

$ pwd   // you should see your ‘present working directory’ printed out

$ ls   // you should see the contents of your present directory

$ ls -a   // hm….there’s some files that were hidden before. The -a stands for all

$ cd dirname   // substitute ‘dirname’ with any of the directory names (no extension) that you saw in either of the last two commands; cd = ‘change directory’

$ pwd   // now you should see the directory that you just changed into

$ cd ..   // go back up one level into the directory you were previously in
````


#### Moar shells

We can also get into/out of other shells that we might get packaged with other programs or languages. For example, since our normal shells only really understand Unix or DOS, we get a Python-specific shell that only interprets Python. To access this shell, simply enter the following in your normal prompt:

````$ python   // you should see text followed by >>>, which is the Python equivalent of ‘$’````

Try talking to the Python interpreter:

````
>>> 1 + 3   // should print 4
>>> pyladies = ‘awesome’   // prints nothing--just setting a variable!
>>> print pyladies   // prints ‘awesome’ (Aw, thanks guys!)
>>> import math   // just imported the python math module. Now we can use all it’s functions!
>>> from math import pi   // import only the ‘pi’ function from math
>>> print pi   // 3.14……
````

To exit the Python shell, simple enter the following at any time:

````>>> exit()````


### Installs

Before we go any further, let’s get our environments ready. We’ll all need to make sure that we’ve got Python 2.7x, pip, and virtualenv installed. Please use the appropriate link below and read the instructions carefully. Reach out and ask if you have any trouble with this!!

Link to Mac OSX install instructions: [https://github.com/florapdx/pyladies_guides/blob/master/mac_installs.md](https://github.com/florapdx/pyladies_guides/blob/master/mac_installs.md)

Link to Windows install instructions: [https://github.com/florapdx/pyladies_guides/blob/master/windows_installs.md](https://github.com/florapdx/pyladies_guides/blob/master/windows_installs.md)

So, we’ve all installed a few programs. What are they?

__pip__: the Python package manager. Using pip, you can install any package listed in Python’s official package registry [https://pypi.python.org/pypi](https://pypi.python.org/pypi). To install a package, simply run
````
$ pip install package_name   // install a package
$ pip uninstall package_name   // uninstall a package
$ pip install --upgrade package_name   // upgrade a package
````

__virtualenv__: Virtualenv is a program that allows us to create separate environments for each of our projects. Say you’ve got one project that you’re working on that requires the newest version of Django, and another that is dependent on an older version. Virtualenvs allow you to download dependencies into a project’s environment so that they don’t pollute all your other projects. The beauty of virtualenv probably won’t be immediately clear, but believe us--you’ll learn to love it!

Let’s create a place to hold our Virtualenvs and a place for our projects. First, use the ‘cd’ command to navigate to a directory where you want to store your projects (or just create these in your home folder by entering ‘$ cd’ with no arguments.

````
$ mkdir Projects   // make a directory called ‘Projects’ (name as you like)
$ cd ..   // navigate back up to the previous directory
$ mkdir Virtualenvs   // make a directory to hold your virtualenvs alongside your projects folder
$ mkdir -p Virtualenvs/pyladies  // make a directory for our virtualenv called ‘pyladies’ inside Virtualenv
$ virtualenv Virtualenvs/pyladies   // you should see some output as your virtualenv is being built
$ source Virtualenvs/pyladies/bin/activate   // You should see (pyladies) to the left of your command prompt. This means you’ve successfully activated your virtualenv
````

## DOGE FTW:

Now that we’ve activated our virtualenvs, we can have some real fun. Because we’re in our active virtualenv, the following will install and only be available within it:

````
$ pip install doge   // you should see some output saying install was successful
$ doge   // many dog! wow!
$ doge --help   // almost all programs will list out their in-built commands with the --help option. Try some!
$ doge --shibe doge-xmas.txt   // all the hacker! pretty data!
````

### Exit your virtualenv when you're done; reactivate again later

````
$ deactivate   // deactivates so you're no longer in that project's env
$ source Virtualenvs/pyladies/bin/activate   // reactivates when you're ready to work in your env again. Remember that you must cd into the directory containing your Virtualenvs directory for this to work!
````
