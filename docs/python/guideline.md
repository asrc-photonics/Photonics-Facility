Here, we will provide you with the list of programs and modules for python you need to install for this course.

## Install python 3.13

Regardless of your operating system, you can download python 3.13 [here](https://www.python.org/downloads/release/python-3133/). For example, for windows we would recommend you to download the recommended file for windows **Windows installer (64-bit)**.

- On windows machines you can also download it from the [Microsoft store](https://apps.microsoft.com/detail/9pnrbtzxmb4z?hl=en-US&gl=US).

- On MacOS you can also install python through [Homebrew](https://brew.sh/) or [MacPorts](https://www.macports.org/install.php):

```
brew install python@3.13
```
or 
```
sudo port install python313
```

- On linux, you can install in from the source. Alternatives methods depend on your distribution. On ubuntu try 

```
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt install python3.13 python3.13-venv
```

- on Fedora and Red Hat
```
dnf install python3.13 
```

- on arch linux
```
sudo pacman -S python
```

Alternatively, you can also install python using [Anaconda](https://www.anaconda.com/download), which is a popular and comprehensive open-source distribution of the Python and R programming languages, specifically designed for data science, machine learning, and artificial intelligence. It bundles these languages with a vast collection of data science packages, as well as tools for managing environments and packages, simplifying the process of setting up and using these technologies. 



## Create a folder: PyPAC 
Create a folder/directory called **PyPAC** (from Python for Photonics Automation and Control) wherever you want in your system. This will be your working folder for this course. Go inside the folder and open the terminal on linux or MacOs or the command prompt on Windows (start up, and look for **cmd**). If not already there, move into that folder using **cd**. Example: If you create the folder in the Desktop and your terminal or command prompt is open in your home folder, you can write:

- On windows
```
cd Desktop\PyPAC
```

- On linux and MacOS
```
cd Desktop/PyPAC
```

## Create virtual environment: env

Now, we will create a virtual environment using [venv](https://docs.python.org/3/library/venv.html). This will make it easy to try different packages or python modules. Moreover, it will help you keep your python installation organized.

- On windows:
```
py -3.13 -m venv env
```

- On linux and MacOS:
```
python3.13 -m venv env
```
Now you should have a folder called **env** inside **PyPAC**

- If you are using Anaconda

```
conda create --prefix ./env  python=3.13
```

### Activate the virtual environment

- On the windows command prompt type:
```
env\Scripts\activate
```

- On linux and MacOS:
```
source env/bin/activate
```

- If you are using Anaconda
```
conda activate ./env
```

If nothing failed, your current line on the terminal or command prompt should start with **(env)**.

### Testing the virtual environment

To test the virtual environment, type python on the terminal or command prompt and press enter. The python shell should appear on the terminal. You will see something like this on ubuntu:

```
Python 3.13.3 (main, Apr  9 2025, 08:55:03) [GCC 13.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
```

For windows, MacOs, or other linux distributions you should see something similar.

Now you can type in the python shell

``` py
print("Hello World!")
```

and press enter. It will output:
```
Hello World!
```

Type **exit()** and press enter to leave the python shell. Your current line on the terminal or command prompt should start with **(env)**.
You can also type the previous program into a file. For that type in the terminal or command prompt

- On windows write
```
notepad hello.py
```

On linux and MacOS write

```
nano hello.py
```

Now type 

``` py
print("Hello World!")
```
In the text editor window, save and close it (Note: with nano you can do **control+o** to save and **control+x** to exit). To run this code, type in the terminal or command prompt window:


```
python hello.py
```

which will output:
```
Hello World!
```

## Update pip

Now type 

```
pip install --upgrade pip
```
to update pip. On windows you might need to type

```
python.exe install --upgrade pip
```
instead. Pip will tell you what to write if there is a problem.



## Python Packages

Now, let us start installing some python packages. Open the terminal or command prompt and activate your environment if you close it for some reason. 

Firstly, we will install three of the most used python packages in academia
```
pip install matplotlib numpy scipy
```

These are used to make plots, do scientific calculations, and statistical analysis (read more here [numpy](https://numpy.org/), [scipy](https://scipy.org/), and [matplotlib](https://matplotlib.org/)).

Next we need to help python to recognize and read for the usb ports of your computer. We need a library named libusb-1.0. While there are many ways to install this library, the easiest ways we found are the following.

- On windows, you need to go to [libusb](https://libusb.info/) and mouseover **Downloads** and select the second option **Latest Windows Binaries**. Extract the file and choose the appropriate **.dll**. Example: **Downloads\libusb-1.0.29\VS2022\MS64\dll\libusb-1.0.dll**. Copy this file and paste it in **This PC\Windows(C:)\Windows\System32**

-On several linux distributions, it is probably already installed. If not, just do 

```
sudo apt install libusb-1.0
```

-On MacOs,

```
brew install libusb
```

Then install the python module [pyusb](https://github.com/pyusb/pyusb)
```
pip install pyusb
pip install zeroconf psutil
```
You can also install [zeroconf](https://pypi.org/project/zeroconf/) and [psutil](https://pypi.org/project/psutil/). Without them, you might get some warnings when looking for devices. They are not necessary though.

To test the pyusb installation open the python shell (by pressing python on the terminal or command prompt):
and type:

```
import usb

for dev in usb.core.find(find_all=True):
    print(dev)
```
And press enter. The python shell should now be filled with a list of ports and information about them. Press **exit()** to leave the python shell.

Now, we are ready to install [PyVISA](https://pyvisa.readthedocs.io/en/latest/) and 
[PySerial](https://pyserial.readthedocs.io/en/latest/pyserial.html#overview):

```
pip install PyVISA  PyVISA-py pyserial
```

If you want to use PyVISA you need to install [National Instruments’s VISA library](https://www.ni.com/en/support/downloads/drivers/download.ni-visa.html#565016) or [PyVISA-Py](https://pyvisa.readthedocs.io/projects/pyvisa-py/en/latest/) which is a pure Python implementation of the VISA standard. For this workshop PyVISA-Py is enough


Finally, we want to install two modules to control a few Thorlabs devices, a [linear stage](https://github.com/roesel/elliptec) and a [powermeter](https://pypi.org/project/ThorlabsPM100/):

```
pip install elliptec ThorlabsPM100
```

- On windows, you also want to install the thorlabs software for the [PM100D powermeter](https://www.thorlabs.com/newgrouppage9.cfm?objectgroup_id=3341&pn=PM100D). In particular you want to install the Thorlabs driver switcher program, that comes also with the software for the power meter. You can look for  the driver switcher at the start up.

- On ubuntu and similar linux distros you might not have permissions to read the devices. Use **sudo** or change the permissions (see this [example](https://stackoverflow.com/questions/29427498/how-to-invoke-sudo-password-request-in-python))

Additionally, we want you to build a Graphical User Interface (GUI), for that we will use [PyQT5](https://pypi.org/project/PyQt5/):
```
pip install PyQT5
```

When you work with PyQT, it is a good idea to install [PyQT Designer](https://build-system.fman.io/qt-designer-download): 

- On windows:
```
pip install PyQT5Designer
```

- On ubuntu and similar linux distros, Designer comes with

```
sudo apt-get install qttools5-dev-tools
```

You can also install PyQT5 through apt:

```
sudo apt-get install python3-pyqt5  
sudo apt-get install pyqt5-dev-tools
```

- On MacOS you need to download and install [QT](https://www.qt.io/download-qt-installer). During the installation you need to create a QT account. It should be free. Follow this [video](https://www.youtube.com/watch?v=eR9dNRvcseU) for more details.


## Additional programs

### IDE
You can use any code editor or Integrated Development Environment (IDE) to write your python programs. We would recommend [visual studio code](https://code.visualstudio.com/) Check [this](https://code.visualstudio.com/docs/setup/setup-overview) for installation details. If you installed Anaconda, you can use [spyder](https://www.spyder-ide.org/) also.
