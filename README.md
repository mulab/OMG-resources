# OMG-resources
Lab μ operation &amp; management group learning resources.

## Prerequisites

Make sure you have the following abilities before you can continue to next section.

- [ ] Cross the GFW. You'll need google search for the reset of the requirements. Baidu is a terrible search engine for techniques.
- [ ] Search in English. Prefer searching in English to in Chinese, which will provide much more precise result.
- [ ] Basic programming skills. [Python][python] is the most basic language you should know.
  If you didn't know python at all, pick up [this site][learn-python] and quickly go through the interactive tutorials, including basic and advantage sections.
  If you encounter any problem, never mind, just skip them, since you may not use that knownledge at all, or you may reference to [python doc][python-doc].
  Python 3 is prefered over python 2, but by default, system python is always python 2, so try to know the difference between them, the version's difference should not be of too much trouble.
  Other language that you should take at a glance: [golang][golang], [node][node]
- [ ] Good git skills. Prefere command line interface as a new starter, then mix using cmd and gui.
  Go through [progit][progit], the first three chapters should be read carefully, the remaining chapters can be taken as advantage knowledgement for expert.
  There is a Chinese in-wall version of progit [translation][progit-zh].
  After mastering git(and GitHub), you should fork this project, and thanks to GFM, you can check the checkbox in this readme, for the convinence of tracking your procedure.
- [ ] Master [docker][docker], this is the fundamental components of Lab μ's infrastructure.
- [ ] Linux. For starter, [ubuntu][ubuntu](do not use ubuntu-kylin) is a good choice.
  But if you can afford a macbook, don't hesitate, it will highly improve your efficiency, unless you're expert on Windows & Linux mixing environment.
  If you can't afford a macbook, never mind, just install a secondary system on your notebook if you are windows user. Do not use virtual machine unless you have a powerful pc, but if you can afford a powerful pc, why don't you buy a macbook instead?
  

[python]: https://www.python.org/
[learn-python]: http://www.learnpython.org/
[python-doc]: https://docs.python.org/3/
[golang]: https://golang.org/
[node]: https://nodejs.org/en/
[progit]: https://git-scm.com/book/en/v2
[progit-zh]: http://git.oschina.net/progit/
[docker]: https://www.docker.com/
[ubuntu]: http://www.ubuntu.com/download/desktop

## Tables of Content

- [Docker](#docker)
- [Web](#web)
- [Database](#database)
- [Other](#other)

### Docker

#### Dockerfile

- Reference: https://docs.docker.com/reference/builder/
- DockerHub: https://hub.docker.com/
- Lab μ dockerfile collection: https://github.com/mulab/Dockerfile
  - It's old, and ** most ** of them should not be used in production.
  - But we can improve it by make contributions to the repo!

#### Docker-compose
- Docker-compose(previous known as fig) overview: https://docs.docker.com/compose/
- Docker-compose yml: https://docs.docker.com/compose/yml/
- Docker-compose command line: https://docs.docker.com/compose/reference/docker-compose/

#### Docker-swarm

Months ago, swarm is not stable enough to use, but things must be different now, need further studying.

#### Consul

In Lab μ, we use consul as service discovery. 

- Consul: https://github.com/hashicorp/consul https://www.consul.io/

But it must have changed over the last 3-6 months, and need to be upgrade.

Lab μ consul installation backlog: https://github.com/mulab/intro/wiki/Consul-%E6%8C%87%E5%8D%97

### Web

#### Nginx

In Lab μ, we prefer nginx over apache. (Cauze we are farmiliar with nginx.)

http_core_module: http://nginx.org/en/docs/http/ngx_http_core_module.html

Currently the service discovery relies on dns, but nginx has dns cache, which cause some issues. The solution should be replaced with using consul-template and dynamic generate nginx configs when container changes.

### Database

Although this should be DBA's job, since we do not have dba yet, database is also mantained by ops.
As this is an expert topic, we only list databases that may be used below:

- Mysql
- Mongodb
- Postgre

### Other

#### Supervisord

Although most of the applications run inside docker, and docker has a `restart=always` option, sometimes you need to run some executation outside docker, and since we are not farmiliar with init.d or something like that, we choose supervisord.

some example: http://supervisord.org/configuration.html#program-x-section-example

#### VPN

In Lab μ, we use openvpn to connect all the servers to a local network. Some configuration are needed to make containers on different host discover each other without problem. Typically, container network should be solved by libnetwork, or weave or integrated solutions in etcd/k8s.

Lab μ openvpn installation backlog: https://github.com/mulab/intro/wiki/VPN%E6%8C%87%E5%8D%97
