rpi-timelapse
=============

A timelapse camera controller for Raspberry Pi and Canon EOS 350d (should work with any camera supported by `gphoto2` with minor tweaks.

This fork from the David´s one is to get rid-off the LCD plate and run the Python script alone. Also to test other CANON EOS cameras



Installation
------------

rpi-timelapse uses `gphoto2` and `imagemagick`.  To install these dependencies on your pi:

```
$ sudo apt-get install gphoto2
$ sudo apt-get install imagemagick
```

Run
---

python tl.py


Post-Processing
===============

Here's how to post process the image frames (on Linux, can be run on the Pi itself, but faster on desktop).

Remove flicker if timelapse used many shutter values
----------------------------------------------------

```
for a in *; do echo $a;/opt/ImageMagick/bin/mogrify -auto-gamma $a;done
```

Be careful with `auto-gamma` - it works extremely well for sunset / sunrise but can make very dark areas of the scene very noisy.

Convert the resulting JPEGs to a timelapse movie
------------------------------------------------

```
ffmpeg -r 18 -q:v 2 -start_number XXXX -i /tmp/timelapse/IMG_%d.JPG output.mp4
```



[Demo Video on YouTube (view in HD)](http://www.youtube.com/watch?v=AZbK4acS5Mc)
