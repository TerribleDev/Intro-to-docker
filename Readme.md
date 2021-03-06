## Intro to docker

This is the code for my intro to docker class. These are the materials for an in-person class. I have recorded the class on [youtube](https://www.youtube.com/watch?v=6EGyhDlr8rs). You can also run through it yourself by reading [the story](story.md). You can read more about it on a [blog post I wrote](https://aka.terribledev.io/docker101).

## Getting Started

We first need to setup our machines. Click the link for your OS. Please read below for specific instructions if required. After you have your machine setup read the [intro](intro.md) 

* [Windows 10](https://gist.github.com/TerribleDev/dd424d3d090bcf5634dcf8417411a081)
* [Windows 7](https://gist.github.com/TerribleDev/721fde498ae7e2e17c5c44a9d8e07412)
* [Windows 8, 8.1, Server 2012, Server 2012 R2](https://gist.github.com/TerribleDev/ad0d19734cbf0b5717a2d4e6fef7f011)
* [Ubuntu 14.04](https://gist.github.com/TerribleDev/3e0a8bab68b83fe5ef896a3bf16a85ce)



### macOS Yosemite 10.10.3 or above

if you are on macOS you can `brew cask install docker-toolbox` or you can download the docker [toolbox here](https://download.docker.com/mac/stable/Docker.dmg). You will then need to install [dotnet core](https://www.microsoft.com/net/core#macos). 

I don't have a mac so I couldn't test this, but this script might work so long as you have ruby installed:


```bash

/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap caskroom/cask
brew cask install docker-toolbox

```

### What you will need

if you prefer to not use the scripts I have made you will need the following installed.

* docker-toolbox (win10/macOS only)
-- or --
* Docker
* Docker-Compose
* Docker-machine


### Notes about Windows 7, 8, 8.1, server 2012

Since you are on older verisons of windows you will run the docker kernel as a VM in a [hypervisor](https://en.wikipedia.org/wiki/Hypervisor). Your hypervisors are listed below.

* Win 7 - `virtualbox`
* Win 8, 8.1, 2012 - `hyperv`


We need to create a machine by doing the following. Please note that you must replace MyHypervisor with the hypervisor listed above


```powershell
# powershell
docker-machine create mydock -d MyHypervisor
```

Now when we work with docker we need to first configure our shell to tell docker to use this machine (once per shell instance)

```powershell
# powershell
docker-machine env mydock | invoke-expression
```

You will then need to `docker-machine ls` and take note of your docker machine's IP address. When we launch websites in docker instead of browsing on localhost you will browse to your docker machine's IP address.
