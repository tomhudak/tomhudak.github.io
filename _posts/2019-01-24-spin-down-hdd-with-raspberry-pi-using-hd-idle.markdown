---
layout: post
title:  "Spin down HDD with Raspberry Pi using hd-idle"
date:   2019-01-24 14:00:00 +0100
categories: raspberry pi hd-idle hdd spin down
description:  "A guide on how to make your HDD stop when it is not is use."
comments: true
---

![HDD](/assets/2019-01-24-rpi-wd.jpeg)

Most of the new HDDs should spin down out of the box but sometimes you might realize that your connected USB HDD is still spinning despite you haven't used your favorite Raspberry Pi for a while. So what to do now?

I am using on old WD Elements HDD plugged to a Raspberry Pi 2 Model B with an OSMC installed on it as OS but it should work the same way on newer Raspberry Pis and with other distibutions installed on it as well.

First of all, you might want to try setting up a spindown rule with hdparm using this guide - altough it never worked for me not even with other HDDs.
So if the above method is non efficient for you then the following steps should be executed using your favorite SSH client. Remote to your RPi then execute the following commands in your home folder (credits goes for HTPC guides):

`cat /proc/diskstats`

This should have a similar repsone:

`8 1 sda1 23694 0 2986336 334340 42 5 376 0 0 188230 334210 8 2 sda2 2 0 4 30 0 0 0 0 0 30 30 8 5 sda5 209713 1975 26144754 2945080 263338 27656 53987400 108849960 0`

If there is no such response you cannot use hd-idle unfortunately, then you should try hdparm or sdparm instead.
Run the following commands line by line to install hd-idle:

{% highlight bash %}
sudo apt-get install build-essential fakeroot debhelper -y
wget http://sourceforge.net/projects/hd-idle/files/hd-idle-1.05.tgz
tar -xvf hd-idle-1.05.tgz && cd hd-idle && dpkg-buildpackage -rfakeroot
sudo dpkg -i ../hd-idle_*.deb
{% endhighlight %}

{% highlight c %}
internal class OkMessageHandler : DelegatingHandler
{
    protected override Task<HttpResponseMessage> SendAsync(HttpRequestMessage request, CancellationToken cancellationToken)
    {
        return Task.FromResult(new HttpResponseMessage(HttpStatusCode.OK));
    }
}
{% endhighlight %}