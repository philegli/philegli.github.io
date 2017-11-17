---
layout: article
title: "Getting Docker up and running on a Raspberry Pi"
categories: tutorials
excerpt: "Installing Docker on a Raspberry Pi"
ads: false
share: false
image:
  teaser: rpi.png
---

Installing docker on the Raspberry Pi is nice and easy. There are some security risks associated with installing it this way but providing you fully trust whatever is hosted by the docker team, you can go ahead with the install.

```
curl -sSL https://get.docker.com | sh
```

![_config.yml]({{ site.baseurl }}/images/installing_docker/curl.png)

Now it's time to test and make sure everything is running as it should.

```
docker run hello-world
```
You should see something like this:
![_config.yml]({{ site.baseurl }}/images/installing_docker/hello.png)

This will check to see if there is already a local image called hello-world. If there isn't, it will pull (download) it from [Docker Hub](https://hub.docker.com/_/hello-world/).
It will then spin up a container based on that image.
