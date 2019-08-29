# Connecting a C.H.I.P. Board

Follow the instructions below to connect your device to the [Cloud4RPi](https://cloud4rpi.io) control panel.

## Prerequisites

It is advisable to update your system before installing.

```sh
sudo apt update && sudo apt upgrade -y
```

Install/update the required packages.

```sh
sudo apt install git python3 python3-pip -y
```

You can use alternative methods to [install pip](https://pip.pypa.io/en/stable/installing.html).

!!! Note
    The Cloud4RPi library is compatible with Python 3.2+ and Python 2.7.9+ versions.

## Getting the Cloud4RPi Client Library

Install the library using your preferred Python version. The following command installs and integrates Cloud4RPi with your OS's default Python interpreter (usually Python 3):

```sh
sudo pip3 install cloud4rpi
```

If you are using Python 2, use the following command:

```sh
sudo python2 -m pip install cloud4rpi
```

!!! Note
    For information on how to work with several versions of Python installed, see [Python Documentation](https://docs.python.org/3/installing/).

If you get an error while using **pip**, try to update the **setuptools** and **pip** packages.

```sh
sudo pip3 install --upgrade setuptools pip
```

## Hacking Together some Code

We have prepared sample code for several platforms in the [cloud4rpi-chip-python](https://github.com/cloud4rpi/cloud4rpi-chip-python) repository to demonstrate sending data to the Cloud.

Get Cloud4RPi examples for your device:

```sh
git clone https://github.com/cloud4rpi/cloud4rpi-chip-python.git && cd cloud4rpi-chip-python
```

Before running a sample ([control.py](https://github.com/cloud4rpi/cloud4rpi-chip-python/blob/master/control.py)), remember to replace the `__YOUR_DEVICE_TOKEN__` string with your real device token. Use a text editor (for instance, `nano`) to replace `__YOUR_DEVICE_TOKEN__` with the token displayed at the top of the device page on [cloud4rpi.io](https://cloud4rpi.io/). If you have no token yet, open the [Devices](https://cloud4rpi.io/devices) page, create a device using the **New Device** button in the top right corner, and use its token.

!!! Note
    Install the [CHIP_IO](https://github.com/xtacocorex/CHIP_IO) Python library as described [in its documentation](https://github.com/xtacocorex/CHIP_IO) to use the C.H.I.P.'s GPIO subsystem from Python. If you do not need GPIO, remove the `import CHIP_IO.GPIO as GPIO` line and all `GPIO` references from the [control.py](https://github.com/cloud4rpi/cloud4rpi-chip-python/blob/master/control.py) example.

## Running

Execute the script with a Python interpreter, for example:

```sh
sudo python3 control.py
```

!!! Note
    If you have installed Cloud4RPi to a non-default Python, use the version with the Cloud4RPi library.

If the script output looks right, open the [Devices](https://cloud4rpi.io/devices) page to see if the device status has changed.


## Installing as a Service

You can use our service templates to facilitate service installation. Pass the path to your Cloud4RPi-enabled Python script to the [service_install.sh](https://github.com/cloud4rpi/cloud4rpi-chip-python/blob/master/service_install.sh) script as a parameter.

```sh
chmod +x service_install.sh
sudo ./service_install.sh your_script.py
```

!!! Note
    You need to replace 'your_script.py' with the actual path to your service script.
