202106191923
Tags:
___
### differences between pipes and sockets

Both pipes and sockets handle byte streams, but they do it in different ways...

-   pipes only exist within a specific host, and they refer to buffering between virtual files, or connecting the output / input of processes within that host. There are no concepts of packets within pipes.
-   sockets packetize communication using IPv4 or IPv6; that communication can extend beyond localhost. Note that different endpoints of a socket can share the same IP address; however, they must listen on different TCP / UDP ports to do so.

_Usage_:

-   Use pipes:
    -   when you want to read / write data as a file within a specific server. If you're using C, you `read()` and `write()` to a pipe.
    -   when you want to connect the output of one process to the input of another process... see [popen()](http://linux.die.net/man/3/popen)
-   Use sockets to send data between different IPv4 / IPv6 endpoints. Very often, this happens between different hosts, but sockets could be used within the same host

___
##### Links


---
##### Источники
