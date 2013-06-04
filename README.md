![PushHub logo][logo]

## Forget about platforms. Set your content free.

Creating, sharing, managing and finding content can become very cumbersome when you are managing websites running on various platforms. And putting everything into one system is oftentimes not an option.

Co-developed by UCLA and Six Feet Up, PushHub was designed for large organizations like universities that need to share content across many CMSs.

PushHub enables you to syndicate content across all your web CMSs while keeping the data in sync and under control in a way that RSS can't match.

## Getting Started

This is an example buildout pulling together the [PushHubCore][PushHubCore] and [PushHubSearch][PushHubSearch] applications. Java is required to install the Solr search engine.

```
$ git clone https://github.com/ucla/PushHub.git
$ cd PushHub
$ python2.7 bootstrap.py -v 1.7.1
$ bin/buildout
```

Start up the processes

```
$ bin/supervisord
$ bin/supervisorctl status
pserve                           RUNNING    pid 6404, uptime 0:00:05
search-zeo                       RUNNING    pid 6403, uptime 0:00:05
solr                             RUNNING    pid 6405, uptime 0:00:05
zeo                              RUNNING    pid 6402, uptime 0:00:05
```

Then register the listener support

```
$ bin/reg_listener "etc/paster.ini#pushhub" http://localhost:51120/search/update
Registered listener for http://localhost:51120/search/update
```

[logo]: https://www.sixfeetup.com/logos/pushhub.jpg
[PushHubCore]: https://github.com/ucla/PushHubCore
[PushHubSearch]: https://github.com/ucla/PushHubSearch
