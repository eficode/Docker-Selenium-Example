# Docker Selenium Example

It's great to use [docker-compose](https://docs.docker.com/compose/) to build web testing infra and launch tests in a blink.

## Setup

**Versions:**
```
(docker-selenium-rf) docker-selenium-rf % docker-machine version
docker-machine version 0.15.0, build b48dc28d

(docker-selenium-rf) docker-selenium-rf % docker-compose version
docker-compose version 1.22.0, build unknown
docker-py version: 3.5.0
CPython version: 3.7.0
OpenSSL version: OpenSSL 1.0.2p  14 Aug 2018

(docker-selenium-rf) docker-selenium-rf % docker version
Client:
 Version:           18.06.1-ce
 API version:       1.38
 Go version:        go1.10.3
 Git commit:        e68fc7a
 Built:             Tue Aug 21 17:21:31 2018
 OS/Arch:           darwin/amd64
 Experimental:      false

Server:
 Engine:
  Version:          18.06.1-ce
  API version:      1.38 (minimum version 1.12)
  Go version:       go1.10.3
  Git commit:       e68fc7a
  Built:            Tue Aug 21 17:29:02 2018
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
