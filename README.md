# **📡 Fawn Wifi Setup & Management**


Follow these steps to connect the Fawn to Wi-Fi.

----------

## **1. Install ADB (Android Debug Bridge)**

ADB lets you communicate with the device from your computer.

### **Windows**

1.  Download the [Android SDK Platform Tools for Windows](https://developer.android.com/tools/releases/platform-tools).
    
2.  Unzip the folder (e.g., to C:\platform-tools).
    
3.  Add that folder to your **PATH** so you can run adb from Command Prompt or PowerShell.
    
    -   [Guide to updating PATH on Windows](https://www.architectryan.com/2018/03/17/add-to-the-path-on-windows-10/).
        
    
4.  Open **Command Prompt** or **PowerShell** and check:
    

```
adb version
```

  

  

### **macOS**
Run these commands in Terminal one at a time 
```
brew install android-platform-tools
adb version
```
Or download the [Android SDK Platform Tools for Mac](https://developer.android.com/tools/releases/platform-tools).

### **Linux (Ubuntu/Debian)**

```
sudo apt update
sudo apt install android-tools-adb -y
adb version
```

----------

## **2. Connect to the Device**

1.  Plug the device into your computer with USB.
    
2.  Check that it’s visible
       - Open Terminal (MacOS) or Windows Terminal and run `adb devices`

If the device does not show up, unplug it and plug it back in and wait 30 seconds. Then try `adb devices` again. 

2.  If you see 'unauthorized', confirm the prompt on the device screen.        
    
3.  Open a shell in root:

> run these one at a time

```
adb root
adb shell
```
----------

## **3. Connect Device to Wi-Fi**

Inside the device shell:

1.  List available networks:
    
```
nmcli device wifi list
```   
    
2.  Connect to Wi-Fi:

> Replace **NETWORK** with your Wi-Fi name (SSID) and **PASSWORD** with the password.

```
nmcli device wifi connect "NETWORK" password "PASSWORD"
```
    
2.  Verify the connection:

```
nmcli device status
```
3. Restart Fawn
> run these one at a time
```
systemctl restart fawn 
exit 
```
✅ Now the Fawn should be online via Wi-Fi. Run this process again to add Fawn to new wifi networks. Email jon@fawnfriends.com and peter@fawnfriends.com if you run into any challenges.

## Troubleshooting 

Fawns can become unresponsive when moving between wifi networks. If moving between known wifi networks ```systemctl restart fawn``` typically resolves the issue. If on a new network, use the instructions above and Fawn will become response once on the new network and restarted. 

If all else fails, try ```systemctl reboot``` after ```adb shell``` to restart Fawn.   

