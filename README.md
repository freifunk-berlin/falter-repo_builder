## Overall Project Structure and Falter Repositories
The Falter project is split into different repositories. For the beginning there are three main repositories you should know:

+ **[packages](https://github.com/Freifunk-Spalter/packages/)**: This repo holds the source code for an OpenWrt package feed. All falter specific packets reside there, regardless if they are luci-apps or just command-line-apps. *Everything* should be bundled as a package. If you want to file an issue or fix a bug you probably want to go here.
+ **[repo_builder](https://github.com/Freifunk-Spalter/repo_builder)**: In that repo there is a script which compiles the source codes from *packages* repo into a package feed. We use the dockerized OpenWrt-SDK for that.
+ **[builter](https://github.com/Freifunk-Spalter/builter)**: The builter assembles Freifunk images from the OpenWrt-imagebuilder and the pre-compiled package feed from repo-builder. If you want to include a new app into falter, you'd need to add it to the packagelists defined here.


# repo_builder
This is a toolchain which aims to build the falter feed in an automated fashion. There is nothing fancy going on here, just a couple of shell scripts which instrument the dockerized OpenWrt-SDK.


## Prerequisites

* Docker
* Python module docker-hub (pip3 install docker-hub)


## How to Get Started?

```sh
#!/bin/bash

./build_all_targets 19.07.7 "src-git falter https://github.com/Freifunk-Spalter/packages.git;spo/master" /tmp/bin/
./publish "/tmp/bin/" "/var/www/html/" "19.07" "falter"
```
