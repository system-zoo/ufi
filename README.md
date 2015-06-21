# Overview

* A canary is a bird.  
* Miners used to carry canaries down in the mine tunnels with them, if the
  birds died that indicated the presence of dangerous gases, and the miners
  would exit the mines immediately.
* In the software industry canary testing is deploying a new version of an
  application to a small number of end users to make sure it works in a real
  world environment. If the new code is buggy the changes can be reversed
  quickly.

For the 2015 Hackathon of the our team decided to implement a canary testing
system with Docker containers and piecing together some existing software. In
the effort to build ship and run.

# Software diagram

![software diagram](System-zoo.png)

# Software technologies used

### Runner
  * [Go](https://golang.org/)
  * [Docker](https://www.docker.com/)

### Proxy
  * [Scala](http://www.scala-lang.org/index.html)
  * [Consul](https://www.consul.io/)
  * [Registrator](https://github.com/gliderlabs/registrator)

### Controller

### Controller UI
  * Node
  * jQuery
  * Bootstrap

### Test-services
  * [Docker](https://www.docker.com/)

### Monitor
* Heka
* [Elasticsearch](https://www.elastic.co/products/elasticsearch)

### Virtual Machines
* Deployed by Juju on Amazon

# Team

* [Whit Morriss](https://github.com/whitmo)
* [Wayne Witzel III](https://github.com/wwitzel3)
* [Kapil Thangavelu](https://github.com/kapilt)
* [Matt Bruzek](https://github.com/mbruzek)
* [Mike Ebinum](https://github.com/mebinum)
* [Mitch Ruebush](https://github.com/mruebush)
* [T.J. Corrigan](https://github.com/tj-corrigan)
* [Deep Mehta](https://github.com/deepmehtait)
* [Chad @tass6773](https://github.com/tass6773)
* [@n8foo](https://github.com/n8foo)

# Communication
The official IRC channel for the Hackathon project is `#systems-zoo` on the
chat.freenode.net server.

# How does it work?

# What does it measure?

# Details

## Payload for elastic search

### - container response payload

```json
{
   "containerid": "0b0c75dc3a5e",
   "requestdate": "2015-06-21",
   "requesttime": "01:56:59",
   "containername": "hopeful_stallman",
   "response": {
      "request": 126,
      "duration": 2500,
      "response": 126,
      "code": 500
   }
}
```

#### Docker machine metrics

```json
{
   "0b0c75dc3a5e9849954be2d18a32481e95874af325cc3b16cd389e5d8a0a7e9f": {
      "newtork_in": "172.17.0.12",
      "containername": "hopeful_stallman",
      "ip": "172.17.0.12",
      "cpu_user": 9.42,
      "cpu_system": 1.39,
      "status": "172.17.0.12",
      "memory": "164777984",
      "cpu_all": 10.81,
      "newtork_out": "172.17.0.12"
   },
   "58a94dafc6c505df9b1eb6b6184f46b2c8f63b71202e301bc029103f8d253c34": {
      "newtork_in": "172.17.0.18",
      "containername": "sharp_elion",
      "ip": "172.17.0.18",
      "cpu_user": 3.23,
      "cpu_system": 0.54,
      "status": "172.17.0.18",
      "memory": "154255360",
      "cpu_all": 3.77,
      "newtork_out": "172.17.0.18"
   },
   "0d35e265adbfc2db737f8e142398a0e91634f5387d42c73833b9cfbdab4367bf": {
      "newtork_in": "172.17.0.14",
      "containername": "tender_fermat",
      "ip": "172.17.0.14",
      "cpu_user": 0.36,
      "cpu_system": 0.28,
      "status": "172.17.0.14",
      "memory": "856064",
      "cpu_all": 0.64,
      "newtork_out": "172.17.0.14"
   },
   "50f9a1e1b035f8c21684ea418d89b48e99b88a523ad7b23c9cd762131758c290": {
      "newtork_in": "172.17.0.3",
      "containername": "mynginx1",
      "ip": "172.17.0.3",
      "cpu_user": 0.01,
      "cpu_system": 0.01,
      "status": "172.17.0.3",
      "memory": "1388544",
      "cpu_all": 0.02,
      "newtork_out": "172.17.0.3"
   }
}
```

#### Route information
```json
{
  "mirrorMode": false,
  "revisions": [
  {
    "revision": 1,
    "trafficRatio":0.9,
    "primary": true
  },
  {
    "revision": 2,
    "trafficRatio":0.1,
    "primary": false
  }
  ]
}
```
