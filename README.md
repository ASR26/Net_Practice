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
| **Next hop**             | This is the first IP which our packets will reach on his way to the target. This way the routing becomes shorter and easier to understand for us. |

## Mask and IP example

Let us say that we have 2 computers which we want to be connected, in order to do this we have to assign them IP which are in the same group, and this group will be defined by the mask.

Computer 1 (C1) has an IP `150.20.10.7` and its mask is `255.255.255.128` or `/25`. If we want the Computer 2 (C2) is able to connect to C1 we need to give it a similar mask so it will be `255.255.255.128` or `/25`, but what about the IP?

This mask means that from `150.20.10.1` to `150.20.10.126` are a subnet and from `150.20.10.129` to `150.20.10.254`, this is because `150.20.10.0` and `150.20.10.127` are reserved for local and broadcast for the first subnet and `150.20.10.128` and `150.20.10.255` for the second subnet.

After this, we know we can only give an IP from the first half to <code>C2</code>, for example `150.20.10.10`. If we give it an IP from the second half, like `150.20.10.240` these two computers could not connect.

## Exercises

<details>
  <summary>Exercise 1</summary>
  In this exercise we have 2 pairs of computers that we want to connect, all of them have a locked mask, so we have to assign a proper IP in order to connect.
  
  - <code>A</code> has a mask <code>255.255.255.0</code> so the first 3 bytes must be equal to <code>B</code> IP and we can give any number to the last byte between 1-254, obviously avoiding the IP taken by B1, for example <code>104.96.23.250</code>.
  - <code>D</code> has a mask <code>255.255.0.0</code> so the first 2 bytes must be equal to <code>C</code> IP and we can give any number to the last 2 bytes between 1-254, obviously avoiding the IP taken by <code>C</code>, for example <code>211.191.1.74</code>.
  
  ![](/sol_img/Level_1.png)
 </details>

<details>
  <summary>Exercise 2</summary>
  In this exercise we have 2 pairs of computers that we want to connect, 3 of them have a locked mask, so we have to assign a proper mask and IP in order to connect.
  
  The masks must be similar between the computers we want to connect and the IP must be in the same group
  
  - <code>B</code> needs the mask of <code>A</code> so we will give it <code>255.255.255.224</code> or <code>/27</code>.
  - <code>A</code> needs an IP in the same group of <code>B</code> so we will give it one in its group, for example <code>192.168.98.221</code>.
  - <code>C</code> and <code>D</code> have their mask locked and because they can only have 4 IP in a group and 2 of them are reserved we need to give them 2 IP which are adjacent and are not reserved, for example <code>192.168.98.1</code> and <code>192.168.98.2</code>
  
  ![](/sol_img/Level_2.png)
 </details>

<details>
  <summary>Exercise 3</summary>
  In this exercise we have 3 computers connected by a switch, as it is explained earlier, a switch works as a multiplier so it allows connection between more than 2 devices, but all of them must be able to connect as usual.
  
  The masks must be similar to C which is locked, and it let us a 128 IP range for the subnet.
  
  - <code>A</code> has its IP locked so the rest of them must be in the same group. Since it is in the first half of <code>104.198.14.X</code> all of them must be between 1 and 126.
  
  ![](/sol_img/Level_3.png)
 </details>
 
 <details>
  <summary>Exercise 4</summary>
  In this exercise we have 2 computers connected by a switch to a router, as it is explained earlier, a router allows connection between more than one devices even if they are not in the same subnet.
  
  We have to use similar IPs to <code>A</code>, but some of them are taken by the router subnet:
  - <code>R2</code> takes from <code>82.168.118.0</code> to <code>82.168.118.127</code>.
  - <code>R3</code> takes from <code>82.168.118.198</code> to <code>82.168.118.255</code>.
  It only let us from <code>82.168.118.128</code> to <code>82.168.118.197</code> so we will give <code>R1</code> and <code>B1</code> IPs in that range, for example <code>82.168.118.130</code> and <code>82.168.118.133</code>, and will set the mask to <code>/26</code> or <code>255.255.255.192</code>
  
  ![](/sol_img/Level_4.png)
  
 </details>
 
 <details>
  <summary>Exercise 5</summary>
  In this exercise we have 2 computers connected by a router, but, in this case we need to set the routing tables. These routing tables only have 2 parameters, the target (left) and the next hop (right).
  
- <code>R2</code> and <code>B</code> must have the same mask. Its IPs must be in the same group, for example <code>139.181.194.252</code>.
- <code>R1</code> and <code>A</code> must have the same mask. Its IPs must be in the same group, for example <code>39.31.71.121</code>.
- The routing table <code>B</code> must have <code>R2</code> IP as next hop.
- The routing table <code>B</code> must have <code>R1</code> IP as next hop and <code>B1</code> IP as target, with the following format <code>XXX.XXX.XXX.XXX/YY</code>, being <code>X</code> the IP and <code>Y</code> the mask.
  
  ![](/sol_img/Level_5.png)
 </details>
 
  </details>
 
 <details>
  <summary>Exercise 6</summary>
  In this exercise we have 2 computers connected by a router, but, in this case we need to set the routing tables. These routing tables only have 2 parameters, the target (left) and the next hop (right).
  
  
  ![](/sol_img/Level_6.png)
 </details>
