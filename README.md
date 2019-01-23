# Docker Selenium Example

It's great to use [docker-compose](https://docs.docker.com/compose/) to build web testing infra and launch tests in a blink.

## Setup

**Versions:**
```
(docker-selenium-rf) docker-selenium-rf % docker-machine version
docker-machine version 0.16.1, build cce350d

(docker-selenium-rf) docker-selenium-rf % docker-compose version
docker-compose version 1.23.2, build unknown
docker-py version: 3.6.0
CPython version: 3.7.2
OpenSSL version: OpenSSL 1.0.2q  20 Nov 2018

(docker-selenium-rf) docker-selenium-rf % docker version
Client: Docker Engine - Community
 Version:           18.09.1
 API version:       1.39
 Go version:        go1.11.4
 Git commit:        4c52b90
 Built:             Thu Jan 10 03:21:29 2019
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
Connect with vnc to the browsers (in 5900 and 5901). When prompted for password the default is `secret`.

## Cleanup
```
docker-compose down
docker-machine rm -f test-machine
```
