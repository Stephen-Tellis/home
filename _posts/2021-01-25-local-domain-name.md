---
layout: page
title:  "Get your own domain on your network"
subtitle: ""
date:   2021-01-16 21:21:21 +0530
categories: ["Linux, Web Dev, Networking"]
---

Clearly, this is not the way to go if you want to stream media from your laptop on your smartphone(plex media server or the many others on offer are the way to go), but, say you want to make a simple database and want everyone who enters and leaves your office to register themselves as means to trace them(e.g: tracing) or you want to switch off or run some other commands on your computer from your bed and have only your phone with you *(Guilty)*. This is then, a good solution as you don't have to always wonder what your IP is.

First run the command `sudo apt install avahi-daemon` to install avahi daemon on your deb linux. This may have been pre installed.

At this point, your server is already running and you can reach it with `<hostmane>.local`  provided your machine has something to serve(or you can SSH into it with this instead of writing the IP) 

If you don't want your hostname as the first half, edit the configuration file located at `/etc/avahi/avahi-daemon.conf` you can use your favourite text editor(Example: With nano on terminal: `nano /etc/avahi/avahi-daemon.conf`)

Now, first uncomment and then change the `host-name=` in the conf file to anything you like (no spaces and no special characters). I changed it to `host-name=tellis`

I'd recommend you leave the .local as it is

<img src="{{ '/assets/img/avahi_conf.png' | prepend: site.baseurl }}" id="pimg">

Now, save the document and restart your machine. Your server is now running with your personal domain name!

How do we test this then? one way is to setup a simple website and access it with your computer as the server. Let me show you. the code is less than 10 lines long.

```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'
    
if __name__ = "__main__":
	app.run(host='0.0.0.0')
```

Install flask (pip install Flask) and run this on your computer. You can now access your website from anywhere on your network by typing `<whateveryournamed>.local` (Example for me: tellis.local)

Ideas? comments? suggestions for improvement?   
Feel free to reach me on my E-mail