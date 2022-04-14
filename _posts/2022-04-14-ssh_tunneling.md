---
layout: page
title:  "Ssh Tunneling"
subtitle: "Unleashing the potential of a remote host, locally"
date:   2022-04-14 21:21:21 +0530
categories: ["Linux, Web Dev, Networking"]
---

The very concept of SSH has fascinated me from the day I learnt about it and it continues to do so every time I use it.  

A tool like SSH (and it's sibling SCP) opens so many doors for you as an innovator and a developer that it just cannot be ignored.  

Clearly, it is quite a mature tool at this point and is already well integrated in most frameworks such as 
- ROS where you can launch nodes on a remote machine. (A good example of this feature is the Universal Robots ROS driver) 
- IDEs such as Visual Studio Code have built on top of it to an extent where you can SSH into a remote machine and develop on it as if you were editing locally (With extensions support, linting, debugging and everything!!! the full IDE experience!!!)

If you are still not convinced, here is a simple example of how powerful even a simple ssh tunnel can be.  

I have 2 machines with me 
1. powerful_machine
2. puny_machine  

with jupyter notebook server running on the localhost of the powerful_machine.

Now, if I wanted to train a machine learning model on the *powerful_machine* and I was working on the *puny_machine* (because this is probably a laptop and I want to chill on the couch with it. *Relatable no???*). I could simply do the following:
```
ssh -L 8888:localhost:8888 <user_on_powerful_machine>@<host_of_powerful_machine>
```
And that is it!  
You have successfully tunneled your jupyter notebook's server from the *powerful_machine* to the *puny_machine*.  
All you have to do now is go to the default address in your browser (on the *puny_machine*) and BAM! jupyter notebook with all the computing capacity of the *powerful_machine* at your service.

How cool and most importantly **simple** was that!

Note, I am assuming you have started your jupyter notebook on the default port and not configured it to start on 0.0.0.0 instead of localhost. In which case it would be available to you already at the IP of the server, but, the biggest caveat being that anybody in your network could tap into whatever you are working on unless you have setup a password to access the jupyter server as well (which is, in my opinion a lot of work).

While the tunnelling setup works beautifully, I would not use this as a permanent solution because:
1. The standard editor/juptyter notebook itself, which frankly, I don't even prefer using natively let alone remotely. I feel like the notebook implementation of VSCode is far more superior and feature rich.
2. As mentioned in the start of the article, you can simply ssh into the machine via VSCode and develop as if you were natively running the same. You are not limited to jupter notebooks nor are you stuck with their default editor


Ideas? comments? suggestions for improvement?
Feel free to reach me on my E-mail




