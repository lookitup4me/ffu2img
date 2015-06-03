# Installing Windows 10 on Raspberry Pi 2 using your Mac

Follow the instructions on Microsoft's site http://ms-iot.github.io/content/en-US/win10/SetupRPI.htm

Near the end, when you need to install the OS onto the SD card, follow a few different steps. Basically, after you unzip the downloaded file, you will find a file called Flash.ffu. This is in a format that cannot be reliably written to the SD card using dd. So use this script (credit to https://github.com/t0x0/random/wiki/ffu2img ) to convert the ffu to img.

Check your python version, I had python 2.x. So my command was

```
python ffu2img.py Flash.ffu RPi.img

```

Insert your SD card. Locate it using
```
diskutil list
```

In my case it was /dev/disk3. You should not just eject it from Finder. It won't do it right. Instead do this.
```
diskutil unmountdisk /dev/disk3
```
Then copy the image with dd
```
sudo dd if=RPi.img of=/dev/disk3 bs=2m
```



ffu2img.py   - python script to convert Microsoft FFU files to raw disk images (tested with python 2.7.9)

ffu2img.py3  - python script to convert Microsoft FFU files to raw disk images (tested with python 3.4.3)
