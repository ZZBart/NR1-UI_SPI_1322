 ## Welcome to the NR1-UI_SPI_1322 wiki!
 Inspired by: [diehardsk/Volumio-OledUI](https://github.com/diehardsk/Volumio-OledUI) // 
 This is the Python3 version of [Maschine2501/Volumio-OledUI](https://github.com/Maschine2501/Volumio-OledUI/)
 Modified by [ZZBart/NR1-UI_SPI_1322](https://github.com/ZZBart/NR1-UI_SPI_1322)``Welcome to the NR1-UI_SPI_1322 wiki!




## Supported Displays:
- [x] SSD1322 (grayscale Oled 256x64)



# NR1-UI
[Maschine2501/Volumio-OledUI](https://github.com/Maschine2501/Volumio-OledUI/) building a Network Hifi Receiver from scratch. Main components are a RaspberryPi4 and an HiFi-Berry-Dac. An old Braun T2 Tuner serves as case for the player.
To keep as much as possible from the look of the device he needed an Interface for Volumio. And especialy one that supports a 3,2" ssd1322 SPI Oled with 256x64Pixel.
After doing some research he found diehrdsk/Volumio-OledUI. It fullfills many points on his "wishlist" but not nearly all.
As we all know, the way is the destination, he and i spent some time (much time....) in modifying the original code.
The project is not finished yet... now i'm building my own.




## The Code is modular and has a Setup-Process. For more information please check [Maschine2501/NR1-UI](https://github.com/Maschine2501/NR1-UI)



## [1. Installation steps]
#  1st step:

* download Volumio Image:
```
https://volumio.com/en/get-started/
```
* download "Win32Diskimager": 
```
https://sourceforge.net/projects/win32diskimager/
```
* Insert the SD card into your SD card reader -> Note the drive letter assigned to the SD card. (You can see the drive letter in the left hand column of Windows Explorer, for example G:)
* Run Win32DiskImager utility.
* Select the downloaded Volumio image file
* In the device box, select the drive letter of the SD card. (Be careful to select the correct drive: if you choose the wrong drive you could destroy the data on your computer's hard disk!)
* Click 'Write' and wait for the write to complete.
* Exit the imager and do NOT eject the SD card.

---

# 2nd step:

Prepare the /boot partition:
2 a)

   * Open your File-Explorer/File-Browser and open the SD-Card Folder, which is labled as "boot"
   * Check if there is a .txt file called "userconfig.txt" -> if not, make one (empty**)**

2 b) ssh File:

   * In the SD-Card Folder "boot", create a new textfile without any letters in it.
   * rename the textfile to "ssh" ("newtextfile.txt -> rename -> ssh)

# 3rd step:
Boot the Raspberry Pi up and get PuTTy / KiTTy ready

  *  put sd-card in the raspberry, (connet it to a network) and let it boot
  *  download either PuTTy or KiTTy (ssh clients)
  *  research on how to connect to a Raspberry using ssh [search](https://www.google.com/search?client=firefox-b-d&q=raspberry+connect+by+ssh)
  *  log in to the Pi with ssh, standard user=volumio, standard pw=volumio

# 4th step:
log in to the Web-UI and finish the "first start setup"
if you want to use a HDMI (Touch-) Display, please install The Touch-Display Plugin, in Volumio-Plugin-Menu, first, then:
```
git clone https://github.com/ZZBart/NR1-UI_SPI_1322.git
```
```
bash NR1-UI/install.sh
```

### Now just do a reboot:
```
reboot
```

Here you are, all installed ;)
If something is wrong:
check the journal!


### For NR1UI:

```
sudo journalctl -fu nr1ui.service
```

### For Cava1:
```
sudo journalctl -fu cava1.service
```

### For Cava2:
```
sudo journalctl -fu cava2.service
```

### Stop the service (the program):
```
sudo systemctl stop nr1ui.service
```
```
sudo systemctl stop cava1.service
```
```
sudo systemctl stop cava2.service
```

### Start the service (the program):
```
sudo systemctl start nr1ui.service
```
```
sudo systemctl start cava1.service
```
```
sudo systemctl start cava2.service
```