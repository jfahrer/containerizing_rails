# README

## Getting started
Please make sure to install
* Docker - https://hub.docker.com/search?q=&type=edition&offering=community
* Git - https://git-scm.com/downloads

We will hand out USB sticks with the installers for Mac and Windows to save some bandwidth.

Make sure to create a Docker ID if you don't have one already: https://hub.docker.com/signup

Clone this repository so that we can iterate on it later in the workshop:
```
git clone https://github.com/jfahrer/containerizing_rails
```

### Testing your Docker installation
Run the following command on you system:
```
docker version
```

The output of the command should look similar to this:
```
Client: Docker Engine - Community
 Version:           18.09.1
 API version:       1.39
 Go version:        go1.10.6
 Git commit:        4c52b90
 Built:             Wed Jan  9 19:33:12 2019
 OS/Arch:           darwin/amd64
 Experimental:      false

Server: Docker Engine - Community
 Engine:
  Version:          18.09.1
  API version:      1.39 (minimum version 1.12)
  Go version:       go1.10.6
  Git commit:       4c52b90
  Built:            Wed Jan  9 19:41:49 2019
  OS/Arch:          linux/amd64
  Experimental:     true
```

The important parts here are
* `Version` for the `Client` and `Server` should be `18.09.1` OR `18.09.2`.
  Please update your Docker installation if you are on an older version.
* Under `Server: Docker Engine - Community` make sure that the  `OS/Arch` says `linux/amd64`.
  If you are seeing `Windows` in there, please make sure to switch you Docker installation to run Linux: https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers

### Verifying Docker Compose version
Run the following command on you system:
```
docker-compose -v
```

The output of the command should look similar to this:
```
docker-compose version 1.23.2, build 1110ad01
```

If you are running an older Version of Docker Compose or you are getting a `command not found`, please follow the installation instructions for Docker Compose: https://docs.docker.com/compose/install/


### Pre-loading images
To save even more bandwidth and time, the USB sticks contain various "images" that we will use throughout the workshop. Please open a shell and change into the `images` directory on the USB stick. In there you will run the following commands:
```
docker image load --input ubuntu.tar
docker image load --input redis.tar
docker image load --input postgres.tar
docker image load --input ruby-on-ice.tar
docker image load --input ruby.tar
```

The output should look similar to this:
```
bebe7ce6215a: Loading layer [==================================================>]  90.62MB/90.62MB
283fb404ea94: Loading layer [==================================================>]  15.87kB/15.87kB
663e8522d78b: Loading layer [==================================================>]  11.26kB/11.26kB
4b7d93055d87: Loading layer [==================================================>]  3.072kB/3.072kB
Loaded image: ubuntu:18.04
```

# Assignments
Throughout the workshop you will complete the following assignments:

* [Assignment 1 - Hello World](_assignments/assignment_01.md)
* [Assignment 2 - Your first image](_assignments/assignment_02.md)
* [Assignment 3 - Running Rails](_assignments/assignment_03.md)
* [Assignment 4 - Talking to a service](_assignments/assignment_04.md)
* [Assignment 5 - Integrating Postgres](_assignments/assignment_05.md)
* [Assignment 6 - Utilizing layers](_assignments/assignment_06.md)
* [Assignment 7 - Glueing things together](_assignments/assignment_07.md)
* [Assignment 8 - Iterating](_assignments/assignment_08.md)
* [Assignment 9 - Integrating Sidekiq](_assignments/assignment_09.md)
