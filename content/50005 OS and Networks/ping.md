# Ping
---
## How to use
-   `ping netflix.com` is the easiest and simplest way to ping a server. It will continuously send packets and print out the response (if any). You may press `ctrl+c` to terminate it.
-   It supports several options:
    -   `-c [no_of_packets]`: specify the number of packets that should be sent by `ping` before terminating (otherwise it will continue forever until `SIGINT`[2](https://natalieagus.github.io/50005/ns_labs/lab1_1#fn:2) is sent by `ctrl+c`).
    -   `-s [packet_size]`: set packet size. The default is 56.
    -   `-i [seconds_interval]`: interval of ping packets sent to the destination

## Usage
However, servers may not reply all ping requests. There may be security settings that cause the server to ignore the ping request out of good intention: avoid DDOS attack


#networks 