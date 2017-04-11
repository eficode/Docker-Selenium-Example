# Docker Selenium Example

It's great to use [docker-compose](https://docs.docker.com/compose/) to build web testing infra and launch tests in a blink.

## Setup

**Versions:**
```
(docker-selenium-rf) docker-selenium-rf % docker-machine version
docker-machine version 0.9.0, build 15fd4c7

(docker-selenium-rf) docker-selenium-rf % docker-compose version
docker-compose version 1.11.1, build 7c5d5e4
docker-py version: 2.0.2
CPython version: 2.7.12
OpenSSL version: OpenSSL 1.0.2j  26 Sep 2016

(docker-selenium-rf) docker-selenium-rf % docker version
Client:
 Version:      1.13.1
 API version:  1.26
 Go version:   go1.7.5
 Git commit:   092cba3
 Built:        Wed Feb  8 08:47:51 2017
 OS/Arch:      darwin/amd64

Server:
 Version:      1.13.1
 API version:  1.26 (minimum version 1.12)
 Go version:   go1.7.5
 Git commit:   092cba3
 Built:        Wed Feb  8 08:47:51 2017
 OS/Arch:      linux/amd64
 Experimental: false
```

## Create Fresh Docker Engine (recommended)
[Docker For Mac](https://docs.docker.com/docker-for-mac/) version 1.13 has [knows issues](https://github.com/docker/docker/issues/25305).
It's recommended to use docker-machine to create a clean engine for this example.
```
docker-machine create -d virtualbox test-machine
eval $(docker-machine env test-machine)
```

## Launch

**Test application:**
```
docker-compose up -d demoapp
```

**Test Infra:**
```
docker-compose up -d hub firefox chrome
```

**Robot Framework Tests with browsers:**
```
docker-compose run test-ff
docker-compose run test-gc
```

**Reports:**  
After test run,test output files will appear in [results](results) directory.

**View & Debug Execution:**  
Connect with vnc to the browsers (in 5900 and 5901)

## Cleanup
```
docker-compose down
docker-machine rm -f test-machine
```
