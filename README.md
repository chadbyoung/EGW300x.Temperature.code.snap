[//]: # (Created on: August 18, 2017)
[//]: # (Author: Chad Young)
[//]: # (Contact: chad.young@dell.com)


# Readme for EGW3K-HTS221 snap
This is a snap for the Dell Edge Gateway 3000 which uses the ST Micro HTS221
temperature sensor. The snap runs a python script on Ubuntu Core 16 and returns
the current temperature observed at the sensor. Keep in mind that this sensor
is inside the system and as such measures the temperature "inside the box". This
snap is meant to be used as a reference on how-to create snaps for Ubuntu Core
16 and as such should not be used in a production environment. As with anything
you find on the internet please proceed with caution as you never know when
Gremlins, Goblins, or Trolls will appear.

### What is occurring:

The snap (via python script) will try to find the ST HTS221 sensor on a Dell
Edge Gateway 300X by looking for a specific iio directory with a file labeled
"name" and its contents being "hts221". After finding this directory with said
file, the program will read the int and float numbers in the three files
located here:  

    /sys/bus/iio/devices/iio:device[0,1,2,3]  

The files that are read are:  

* in_temp_raw (int)
* in_temp_offset (int)
* in_temp_scale (float)
  
The int/floats in the files above are then run through the following formula:  
  
    T = (((in_temp_raw + in_temp_offset) * in_temp_scale))  
    Where T is in degrees celsius

## How to install
Install the snap that is created using the --devmode option.  

## How to run
From the command prompt run "egw3k-hts221.temperature"  
  
For questions please email <chad_young@dell.com>

