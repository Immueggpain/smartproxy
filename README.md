## Introduction
[Old README for v0.5.0](README-0.5.0.md) 

When using **smartproxy** as your system's default proxy, it can redirect traffic on user rules, 
whether direct connect or through a smartproxy server.

**smartproxy** accepts HTTP, HTTPS, SOCKS4, SOCKS4a, SOCKS5 as incoming connections.

**smartproxy** also redispatches HTTP requests, so some old HTTP clients without keep-alive support will enjoy some performance boost.

## QuickStart
* Make sure you have **[Java](https://jdk.java.net/11/) 8+** installed
* [Download latest build](https://github.com/Immueggpain/smartproxy/releases). Unzip it
* Run `java -jar smartproxy-x.x.x.jar --help` to get help.
* Run client `java -jar smartproxy-x.x.x.jar -m client -i 127.0.0.1 -n 1083 -p <server_port> -s <server_ip> -w <your secret password>`.
* Run server `java -jar smartproxy-x.x.x.jar -m server -w <your secret password>`.
* Set your system proxy to 127.0.0.1:1083
* Enjoy!

## user.rule
[The lastest user.rule can be downloaded here.](user.rule)  
**smartproxy** automatically uses user.rule file in current working directory as routing configuration.  
```
# A line which starts with "#" is comment
# "a.com" means "a.com" only, ".a.com" means "a.com" and all sub domains of "a.com" 
# we can also use ip range like "192.168.0.0 192.168.255.255"
#
# "direct" means connect without proxy
# "proxy" means forward to backend proxy
# "reject" means drop connection
```
For example, when deciding routes of **sub.domain.com**, smartproxy first checks if there's a **sub.domain.com** rule.  
Then it checks **.sub.domain.com**. Then **.domain.com**. Then **.com**.  
And lastly, if all miss, it uses default rule, which is **proxy**.

## Build
You need [**Maven**](https://maven.apache.org/) to build **smartproxy**.  
Just run `maven install` and you will find the jar and zip generated in the `target` folder.  
You can also import the project using [**Eclipse**](https://www.eclipse.org/).
