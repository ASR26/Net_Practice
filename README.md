# Net_Practice
This proyect consists in routing different devices using [subnets](https://en.wikipedia.org/wiki/Subnetwork), [masks](https://condor.depaul.edu/sjost/361/materials/SubnetMask.html) and [routing tables](https://en.wikipedia.org/wiki/Routing_table).
We will be provided with 10 HTML files which will be the exercises that we have to complete.

## Glossary

| Name | Description |
|------|------------|
| **IP address**    | This is the address of a device which will be used as an identifier so packets can be directed to it. This will be a number with the format `XXX.XXX.XXX.XXX` going from `0.0.0.0` to `255.255.255.255`. |
| **Mask**       | This is a way of partitioning the network into subnets. These masks are necessary for a proper performance. These mask go from `0.0.0.0` to `255.255.255.255` as well. They can be formated that way or like this `/24`, being this number the ammount of bits which are fixed for the subnet. |
| **Switch**     | This is a device which works as a multiplier, it allows connection between more than 2 devices which are in the same subnet. |
| **Router**     | As its name says it routes, which means that it allows connection between 2 or more devices even being in different subnets. In order to do this it will need a routing table. |
| **Routing table**        | This is a set of rules which determine where data packets will be directed. They use to have a lot of parameters such as `destination`, `mask`, `gateway`, `interface` or `metric`, but for this case we only need to know 2 of them: `destination` and `next hop`. |
| **Destination / target** | This is the IP we want to reach through our router, The format will be XXX.XXX.XXX.XXX/XX being the last 2 digits the mask. |
| **Next hop**             | This is the first IP which will reach our packets on his way to the target. This way the routing becomes shorter and easier to understand for us. |

## Mask and IP example

Let us say that we have 2 computers which we want to be connected, in order to do this we have to assign them IP which are in the same group, and this group will be defined by the mask.

Computer 1 (C1) has an IP `150.20.10.7` and its mask is `255.255.255.128` or `/25`. If we want the Computer 2 (C2) is able to connect to C1 we need to give it a similar mask so it will be `255.255.255.128` or `/25`, but what about the IP?

This mask means that from `150.20.10.1` to `150.20.10.126` are a subnet and from `150.20.10.129` t0 `150.20.10.254`, this is because `150.20.10.0` and `150.20.10.127` are reserved for local and broadcast for the first subnet and `150.20.10.128` and `150.20.10.255` for the second subnet.

After this, we know we can only give an IP from the first half to C2, for example `150.20.10.10`. If we give it an IP from the second half, like `150.20.10.240` these two computers could not connect.

## Exercises
