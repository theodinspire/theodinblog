---
title: "Deploying a VM"
date: 2018-05-14T02:24:38-05:00
draft: false
---

Oh boy. Deployment has been quite the hassle. I went through three virtual
machines in the process. The first one I scratched because I corrupted the
`sudoers` file and it being a virtual machine in the cloud, had no real way of
logging into the machine locally. The third machine probably didn't need to be
scrapped, but I had not set up the DNS to the system properly and didn't figure
out why I couldn't see the Jenkins site until after I nuked it.

<!--more-->

It took me four days to figure out what was up, and I poured way too much
personal time into the process. I have already been behind on sleep and some of
the work I did on this was in the middle of the night after having some false
*eureka* moments.

The heart of the issue was a clash between the default set up of Jenkins and the
suggested Linux release of Hugo on Snap. Snap installations are only allowed to
write files into the user directories in the `/home/` folder. However, when
Jenkins is installed the `jenkins` user's home directory is `/var/lib/jenkins`.

Eventually I landed on a simple solution, but it took me a while of bashing my
head against a wall to get there: give the Jenkins user a `/home/jenkins/`
folder to work in. I wound up doing it by making a `jenkins` user account before
installing Jenkins into the VM, but I would now imagine it would work just as
well to `mkdir /home/jenkins/` and  assign ownership of the directory to
`jenkins` after having installed Jenkins. Then, from the Jenkins front end, I
set up the environment to place workspaces into that selfsame directory.

Once I got the kinks figured out though, I was actually surprised at how quiet
the successful build was. This post is actually the test to determine if pushing
into this blog's repository will trigger a build, but if you don't see anything
after this sentence you can assume that I have been successful.

Whelp. I had one more step: set up GitHub to send the payload to my Jenkins
server to trigger the build. Here I go again.
