# Net_Practice
This proyect consists in routing different devices using [subnets](https://en.wikipedia.org/wiki/Subnetwork), [masks](https://condor.depaul.edu/sjost/361/materials/SubnetMask.html) and [routing tables](https://en.wikipedia.org/wiki/Routing_table).
We will be provided with 10 HTML files which will be the exercises we will complete.

## Glossary
**IP address**: This is the address of a device which will be used as an identifier so packets can be directed to it. This will be a number with the format `XXX.XXX.XXX.XXX` going from `0.0.0.0` to `255.255.255.255`.
**Mask**: This is a way of partitioning the network into subnets. These masks are necessary for a proper performance. These mask go from `0.0.0.0` to `255.255.255.255` as well. They can be formated that way or like this `/24`, being this number the ammount of bits which are fixed for the subnet.
**Switch**: This is a device which works as a multiplier, it allows connection between more than 2 devices which are in the same subnet.
**Router**: As its name says it routes, which means that it allows connection between 2 or more devices even being in different subnets. In order to do this it will need a routing table.
**Routing table**: This is a set of rules which determine where data packets will be directed. They use to have a lot of parameters such as `destination`, `mask`, `gateway`, `interface` or `metric`, but for this case we only need to know 2 of them: `destination` and `next hop`.
**Destination / target**: This is the IP we want to reach through our router, The format will be XXX.XXX.XXX.XXX/XX being the last 2 digits the mask.
**Next hop**: This is the first IP which will reach our packets on his way to the target. This way the routing becomes shorter and easier to understand for us.

