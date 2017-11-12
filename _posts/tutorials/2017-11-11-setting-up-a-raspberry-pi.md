---
layout: article
title: "Getting started with a Raspberry PI"
categories: tutorials
excerpt: "Installing raspbian"
ads: false
share: false
image:
  teaser: rpi2.png
---

I've had a number of Raspberry PIs for years now and they're great. I recently managed to corrupt one of the SD cards so I thought I'll document the process of getting the PI back up and running.

## 1) Downloading Raspbian

Go to the [official repository](https://www.raspberrypi.org/downloads/raspbian/) and download the latest Raspbian image. I usually go for the lightweight option as I don't usually connect my Raspberry PIs up to a screen via the HDMI output and use a keyboard + mouse etc.

## 2) Writing Raspbian to an SD card

The last time I did this I was using the command line to do all of this and it all worked fine. This time however I thought I'd give Etcher a go and it worked nicely too!

Etcher runs on Linux, Mac OS, and Windows and can be obtained from their website at [https://etcher.io/](https://etcher.io/).

![_config.yml]({{ site.baseurl }}/images/installing_raspbian/etcher.png)

It really is very easy to use! Select the image you just downloaded in step 1, select the SD card, and press "flash".

One piece of advise though...before flashing the image to the SD, take one last look and make sure you didn't insert the wrong SD.

![_config.yml]({{ site.baseurl }}/images/installing_raspbian/etcher2.png)

## 3) Enabling SSH

Once last step before booting up the Raspberry PI with the new SD. As we'll be connecting to the Pi remotely, we'll have to make sure SSH is enabled. By default, SSH is disabled. To enable it, you can add a blank file called "SSH" to the root of the SD card. This can be done in many ways although I just used ```touch``` from the command line.

![_config.yml]({{ site.baseurl }}/images/installing_raspbian/touch.png)

The SD card is now ready.


## 4) Booting up time!

To boot up the Raspberry PI, first connect the ethernet cable to either a router or other network device and then connect the power.

Soon after, the Raspberry Pi should be up and running.


## 5) Find the IP

To connect to it we of course need to figure out its IP. In my case, I just looked at the list of connected devices on the router but other options are to run a quick nmap scan or similar.

![_config.yml]({{ site.baseurl }}/images/installing_raspbian/ip.png)


## 6) Connecting to the Raspberry PI

Finally we can connect to the Raspberry PI.

Using SSH directly from the terminal or using Putty if you're on Windows, establish a connection using username pi and password raspberry.

```ssh pi@10.10.1.88```

You'll probably get a message such as: The authenticity of host '10.10.1.88 (10.10.1.88)' can't be established and an ECDSA key fingerprint. For now this can be ignored with "yes".

Currently this is quite a vulnerable set-up as it's still using the default username and password so it's time to change this.

## 7) Configuring the Raspberry PI

It's time to carry out some final configuration before doing fun stuff.
Run the configuration utility: ```sudo raspi-config```

The following dialog should pop up:

![_config.yml]({{ site.baseurl }}/images/installing_raspbian/config1.png)

1 is absolutely essential!

2 is up to you if you

3 the default is fine for what we're doing. It boots straight to the cli.

4 in my case I selected en_GB.UTF-8 UTF-8. This is really up to you too.

5,6 N/A

7 This brings up options A1 to A6. A1 is a good idea and you might want to change A3 to a low value too.

![_config.yml]({{ site.baseurl }}/images/installing_raspbian/config2.png)

8,9 N/A

For some of the options to take effect, choose to reboot the Raspberry PI.

![_config.yml]({{ site.baseurl }}/images/installing_raspbian/config3.png)
