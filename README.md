# repo_builder

this is a toolchain which aims to build falter feed in a automated fashion. There is nothing fancy going on here, just a couple of shell scripts, which instrument the dockerized openwrt sdk.


## prerequisites

* Docker
* Python module docker-hub (pip3 install docker-hub)


## how to get started?

```
#!/bin/bash

./build_all_targets 19.07.3 "src-git falter https://github.com/Freifunk-Spalter/packages.git;spo/master" /tmp/bin/
./publish "/tmp/bin/" "/var/www/html/" "19.07" "falter"
```
