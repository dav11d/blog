How to watch Acestream on your Samsung Smart TV.
tech
author: David
time: 12:00

This a is guide for those looking to watch Acestream via Samsung Smart TV. It is written with a notion that you have at least some prior knowledge of working these applications, if not - I'm sure you will find this guide easy enough to follow along.


<!-- SPLIT -->

# Introduction

This a is guide for those looking to watch Acestream via your Samsung Smart TV. 
First I want to make it clear that this is not a direct standalone solution for watching it via your Samsung Smart TV only. You _are_ going to need your computer, but as far as I'm aware this is the best and only option that there is right now without any additional hardware (e.g Amazon Fire Stick)

This has been tried and tested with a Samsung KU64000 although I am almost sure it will work with any compatable Smart TV & computer (windows, mac/linux) that can run Plex.

The basic idea is that you will use Ace Player on your computer to capture the stream that comes in, encode it & cast it to your TV over your local network via Plex, sort of like a proxy.

At the end of this tutorial you may be tempted to try and run Acestream through Plex in your browser before trying it on your T.V. *Be aware* your browser will not run it! So before you think it is not working, try it on your T.V first!

# What you are going to need

- Acestream
- Plex for your computer & Samsung Smart TV.
- IPTV Plugin for Plex [link](https://github.com/Cigaras/IPTV.bundle)

# Installation

Download Acestream for your computer and install it.

Download Plex for your computer and install it.

Download Plex the app for your Samsung Smart TV and install it. (available on the store)

# Ace Player

Once you have everything suitably installed, open up Ace Player on your computer.

Choose ``` Tools > Preferences ```

In the bottom left of the Preferences you will see ``` Show Settings ``` > ```Choose 'All'```

Scroll down in the menu to the left and choose ``` Stream output ```

In the Stream output settings you will see an empty box at the top alongside ``` Default stream output chain ```

In this box copy and paste in: 

``` #duplicate{dst="http{acodec=mpga,vcodec=h264,mux=ts,dst=:8903}",dst=display} 
```

You should now have it looking something like this:

![alt text](http://i.imgur.com/mtAp2Tc.png)

Choose save and it will close the Preferences.

(nb: for me this was the most important I had to get right, I tried a dozen other strings of code with different encoding settings and this is the one that worked. If you find that your TV is having trouble playing the stream, have a play around with the codec options. (e.g vcodec=h264)).



# Plex

Once you have your Plex account setup and your Media Server running, open up your plugin directory usually found at 

```
C:\Users\YOURNAME\AppData\Local\Plex Media Server
```

Alternatively you can right click on your Plex Media Server icon in the taskbar > open plug-ins folder.

Unzip the IPTV.Bundle folder here. (make sure its called 'IPTV.Bundle' and not master at the end)

Next you want to find out the address of your computer running Ace Player on your local network.

It usually looks something like 192.168.0.x

You can find this information on your Wifi connection details (IPv4)

Now you want to create a new file named ```playlist.m3u``` inside

```
C:\Users\YOURNAME\AppData\Local\Plex Media Server\Plug-ins\IPTV.bundle\Contents\Resources
```

In your new file ```playlist.m3u``` you want to set it up so it looks like this (include your own IPv4 address)

```
#EXTM3U
#EXTINF:-1,Acestream
http://192.168.0.x:8903/
```

Save your new file and update your Plex Libraries.

# The Finale

OK you made it this far, thats the hard stuff out of the way so now for the good part.

In Ace player on your computer find an Ace stream of your choice and open it as you would normally > ```Media > Open Ace Stream Content ID```

Your stream should now be playing on your computer.

Open up Plex on your Samsung Smart TV. 

Choose ```Channels > IPTV > Acestream```

If you have done everything correct your stream should now begin playing on your TV!

# Notes

