---
layout: page
title:  "Ssh Tunneling"
subtitle: "Unleashing the potential of a remote host, locally"
date:   2022-04-14 21:21:21 +0530
categories: ["Linux, Web Dev, Networking"]
---

The very concept of SSH has fascinated me from the day I learnt about it and it continues to do so every time I use it.  

A tool like SSH (and it's sibling SCP) opens so many doors for you as an innovator and a developer that it just cannot be ignored.  

Clearly, it is quite a mature tool at this point and is already tightly integrated in most frameworks such as 
- ROS 1 where you can launch nodes on a remote machine
- IDEs such as Visual Studio Code have built on top of it to an extent where you can SSH into a remote machine and develop on it as if you were editing locally (With extensions support, linting, debugging and everything!!! the full IDE experience!!!)

If you are still not convinced, here is a simple example of how powerful even a simple ssh tunnel can be.  

I have 2 machines with me 
1. mighty_machine
2. puny_machine  

with jupyter notebook server running on the localhost of the mighty_machine.

Now, if I wanted to train a machine learning model on the *mighty_machine* and I was working on the *puny_machine* (because this is probably a laptop and I want to chill on the couch with it. *Relatable no???*). I could simply do the following:
```
ssh -L 8888:localhost:8888 <user_on_mighty_machine>@<host_of_mighty_machine>
```
And that is it!  
You have successfully tunneled your jupyter notebook's server from the *mighty_machine* to the *puny_machine*.  
All you have to do now is go to the default address in your browser (on the *puny_machine*) and BAM! jupyter notebook with all the computing capacity of the *mighty_machine* at your service.

How cool and most importantly **simple** was that!  
Jupyter notebook was just an example, the same works for any server.  
Tunneling gives us so much freedom and also lets us develop cool new applications. (including remote-teleop of robots)  

Note, I am assuming you have started your jupyter notebook on the default port and not configured it to start on 0.0.0.0 instead of localhost. In which case it would be available to you already at the IP of the server, but, the biggest caveat being that anybody in your network could tap into whatever you are working on unless you have setup a password to access the jupyter server as well (which is, in my opinion a lot of work).


Ideas? comments? suggestions for improvement?  
Feel free to reach me on my E-mail




