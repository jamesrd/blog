+++
author = "James DeVries"
title = "Garmin Watch Face Development"
date = "2024-03-22"
description = "Getting started with Garmin Connect IQ watch face development"
tags = [
    "garmin", "connectiq"
]
+++

## Overview:

This post is a summary of the information I found to develop a simple
Garmin Connect IQ watch face that displays content in a JSON format. 

![Watch face with JSON layout](fr265.jpg "Watch face content formatted as a JSON document.")

[Source Code](https://github.com/jamesrd/JsonWatch)


## Developer Setup:

You need these installed before installing the Garmin Connect IQ SDK.
1. Java SDK
1. [Visual Studio Code](https://code.visualstudio.com/)

Follow the instructions here: [https://developer.garmin.com/connect-iq/connect-iq-basics/getting-started/](https://developer.garmin.com/connect-iq/connect-iq-basics/getting-started/)
to install the Connect IQ SDK, the Visual Studio Code Monkey C extension and generating a
developer key.

Once the Monkey C extension is verified you can create a new Watch Face project
from the Visual Studio Code command palette.

## Watch Face Contents:

Here are the APIs used to get the information displayed on the watchface:

1. Date and Time:
The `System.getClockTime()` only includes the current time, not date information.
Since the watch face also includes the current date the information is loaded
through the `Gregorian` calendar to get current date and time.
```c
var clockTime = Gregorian.info(Time.now(), Time.FORMAT_SHORT);
```

2. Battery Level:
The battery level can be read from the current `System.Stats` object:
```c
var battery = System.getSystemStats().battery;
```

3. Step Count:
Current steps comes from `ActivityMonitor.Info` which is accessed through
the `ActivityMonitor`:
```c
var stepCount = ActivityMonitor.getInfo().steps;
```

4. Heart Rate:
How heart rate is accessed depends on the device. This logic will first
get the heart rate from `Activity.Info` or reading the most recent value
from the `ActivityMonitor.HeartRateIterator`:
```c
var newHr=Activity.getActivityInfo().currentHeartRate;
if(newHr==null) {
    var hrh=ActivityMonitor.getHeartRateHistory(1,true);
    if(hrh!=null) {
        var hrs=hrh.next();
        if(hrs!=null && hrs.heartRate!=null && hrs.heartRate!=ActivityMonitor.INVALID_HR_SAMPLE) {
            newHr=hrs.heartRate;
        }
    }    	
}
```

5. Notification Count:
The number of unread messages is available in the `System.DeviceSettings` object:
```c
var messages = System.getDeviceSettings().notificationCount;
```

## Installing on Device:

1. Build the `.PRG` file for the watch face by selecting `Build for Device`
from the Visual Studio Code command palette. 
    * Select the product you're building for.
    * Select the folder to put the `.PRG` file in.
1. Connect your watch to the computer.
    * To browse files on the watch you may need to install additional software.
    For instance on macOS I use the [Android File Transfer](https://www.android.com/filetransfer/)
    tool to get access to the file storage on the Garmin watch.
1. Copy the `.PRG` file from your computer into the watch's `GARMIN/Apps` folder
