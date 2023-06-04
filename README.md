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
  </br>
  In this exercise we have 2 pairs of computers that we want to connect, all of them have a locked mask, so we have to assign a proper IP in order to connect.
  
  - <code>A</code> has a mask <code>255.255.255.0</code> so the first 3 bytes must be equal to <code>B</code> IP and we can give any number to the last byte between 1-254, obviously avoiding the IP taken by B1, for example <code>104.96.23.250</code>.
  - <code>D</code> has a mask <code>255.255.0.0</code> so the first 2 bytes must be equal to <code>C</code> IP and we can give any number to the last 2 bytes between 1-254, obviously avoiding the IP taken by <code>C</code>, for example <code>211.191.1.74</code>.
  
  ![](/sol_img/Level_1.png)
 </details>

<details>
  
  <summary>Exercise 2</summary>
  </br>
  In this exercise we have 2 pairs of computers that we want to connect, 3 of them have a locked mask, so we have to assign a proper mask and IP in order to connect them.
  
  The masks must be similar between the computers we want to connect and the IP must be in the same group.
  
  - <code>B</code> needs the mask of <code>A</code> so we will give it <code>255.255.255.224</code> or <code>/27</code>.
  - <code>A</code> needs an IP in the same group of <code>B</code> so we will give it one in its group, for example <code>192.168.98.221</code>.
  - <code>C</code> and <code>D</code> have their mask locked and because they can only have 4 IP in a group and 2 of them are reserved we need to give them 2 IP which are adjacent and are not reserved, for example <code>192.168.98.1</code> and <code>192.168.98.2</code>.
  
  ![](/sol_img/Level_2.png)
 </details>

<details>
  
  <summary>Exercise 3</summary>
  </br>
  In this exercise we have 3 computers connected by a switch, as it is explained earlier, a switch works as a multiplier so it allows connection between more than 2 devices, but all of them must be able to connect as usual (their IP must be in the same subnet).
  
  The masks must be similar to C which is locked, and it let us a 128 IP range for the subnet.
  
  - <code>A</code> has its IP locked so the rest of them must be in the same group. Since it is in the first half of <code>104.198.14.X</code> all of them must be between 1 and 126.
  
  ![](/sol_img/Level_3.png)
 </details>
 
 <details>
  
  <summary>Exercise 4</summary>
  </br>
  In this exercise we have 2 computers connected by a switch to a router, as it is explained earlier, a router allows connection between more than one devices even if they are not in the same subnet.
  
  We have to use similar IPs to <code>A</code>, but some of them are taken by the router subnet:
  - <code>R2</code> takes from <code>82.168.118.0</code> to <code>82.168.118.127</code>.
  - <code>R3</code> takes from <code>82.168.118.198</code> to <code>82.168.118.255</code>.
  It only let us from <code>82.168.118.128</code> to <code>82.168.118.197</code> so we will give <code>R1</code> and <code>B1</code> IPs in that range, for example <code>82.168.118.130</code> and <code>82.168.118.133</code>, and will set the mask to <code>/26</code> or <code>255.255.255.192</code>
  
  ![](/sol_img/Level_4.png)
  
 </details>
 
 <details>
  
  <summary>Exercise 5</summary>
  </br>
  In this exercise we have 2 computers connected by a router, but, in this case we need to set the routing tables. These routing tables only have 2 parameters, the target (left) and the next hop (right).
  
- <code>R2</code> and <code>B</code> must have the same mask. Its IPs must be in the same group, for example <code>139.181.194.252</code>.
- <code>R1</code> and <code>A</code> must have the same mask. Its IPs must be in the same group, for example <code>39.31.71.121</code>.
- The routing table <code>B</code> must have <code>R2</code> IP as next hop.
- The routing table <code>B</code> must have <code>R1</code> IP as next hop and <code>B1</code> IP as target, with the following format <code>XXX.XXX.XXX.XXX/YY</code>, being <code>X</code> the IP and <code>Y</code> the mask.
  
  ![](/sol_img/Level_5.png)
 </details>
 
 <details>
  
  <summary>Exercise 6</summary>
  </br>
  In this exercise we have 1 computers connected by a switch to a router, which connects to the Internet.
  
  - Since <code>R2</code> has a fixed IP and mask we already know its subnet, being <code>163.172.250.0</code> - <code>163.172.250.15</code>.
  - We can set <code>A1</code> mask to <code>255.255.255.128</code> or <code>/25</code> because it is connected to <code>R1</code>.
  - Now let us give <code>R1</code> an IP which is can connect to <code>A1</code>.
  - Internet target must be <code>A1</code> IP and its mask, being <code>67.130.151.227/25</code>.
  - Because <code>R</code> next hop is an IP from R1 subnet we know that its target must be in that way so we set the Internet IP as target.
  - Finally let us set the <code>A</code> routing table, being the target <code>8.8.8.8/16</code>, <code>0.0.0.0/0</code> or <code>default</code>.
  
  ![](/sol_img/Level_6.png)
 </details>

 <details>
  
  <summary>Exercise 7</summary>
  </br>
  In this exercise we have 2 computers connected by 2 routers. <code>R11</code> and <code>R12</code> IPs are locked so we have to work around that. In this exercise we could give almost any size of mask, but I will use <code>255.255.255.128</code> (feel free to try other options).
  
  - Because all the masks will be the same we will set them all now.
  - Now, <code>A1</code> IP must be in the <code>R11</code> subnet so we will give it <code>119.198.14.2</code>, and we already know its next hop so we will set it to <code>R11</code> IP. 
  - Same for <code>R21</code> and <code>R12</code> so we will set <code>R21</code> IP to <code>119.198.14.249</code>, now we can set <code>R1</code> next hop to this IP too.
  - For <code>R22</code> and <code>C1</code> we can use any IP we want except <code>119.198.14.X</code> since all of them are in use. We will use <code>119.198.16.19</code> and <code>119.198.16.20</code>.
  - Now we just have to set <code>A</code> routing table, giving it <code>C1</code> IP, and same for <code>R1</code>.
  - <code>R2</code> and <code>C1</code> will have <code>A1</code> IP as target and their corresponding next hops.
  
  ![](/sol_img/Level_7.png)
 </details>

 <details>
  
  <summary>Exercise 8</summary>
  </br>
  In this exercise we have 2 computers connected by 1 router, this one connects to a second router which connects to the Internet.
  
  - Since we have <code>R12</code> mask and IP locked we can set Internet routing table with this IP.
  - Now, using the next hop in <code>R2</code> routing table we can set <code>R13</code> IP.
  - Let us set R23 mask to <code>255.255.255.240</code> or <code>/28</code> so it can connect to <code>D1</code>.
  - <code>R2</code> <code>C</code> and <code>D</code> routing tables will connect to the Internet so let us give them <code>default</code> or <code>0.0.0.0/0</code> as target.
  - Because the internet will only connect to <code>157.229.44.0</code> IPs, all of our IPs must be in that range so we will set the rest of our masks to <code>/30</code> or <code>255.255.255.252</code> since we only need 2 IPs for each subnet.
  - Now, <code>R21</code> must have <code>157.229.44.61</code> as IP since it is the only one in <code>R13</code> subnet.
  - After this we can set <code>R1</code> routing table, giving it <code>157.229.44.61</code> as next hop and <code>157.229.44.0/26</code> as target, since it is the same as the Internet target.
  - There are only 4 IP left to set so let us give them some that are in the same subnet to each pair, for example, <code>157.229.44.1</code> and <code>157.229.44.2</code> for <code>R23</code> and <code>D1</code>; and <code>157.229.44.21</code> and <code>157.229.44.22</code> for <code>R22</code> and <code>C1</code>.
  - Finally let us set <code>C</code> and <code>D</code> next hop.
  
  ![](/sol_img/Level_8.png)
 </details>
 
  <details>
  
  <summary>Exercise 9</summary>
  </br>
  Because this exercise is longer, harder and needs a lot of connections I recommend to try getting an OK in each goal, one by one.
  
  - Firtly let us set a few IPs and masks that we already know.
  - <code>R23</code> IP must be the one in <code>D</code> next hop.
  - <code>D1</code> mask must be the same as <code>R23</code>.
  - <code>A1</code> and <code>B1</code> masks must be the same as <code>R11</code>.
  - <code>R13</code> mask must be the same as <code>R21</code>.
  - Now we have to connect <code>A1</code> and <code>B1</code>, but this is kind of tricky, because <code>A1</code> will be connected to the internet so its IP cannot be <code>192.168.X.X</code>, so let us set them to <code>192.18.14.3</code> and <code>192.18.14.5</code>, and since we will need it later let us set <code>R11</code> to <code>192.18.14.1</code>.
  - After this, we need to connect <code>C1</code> and <code>D1</code>. These two have a similar problem, since <code>10.0.0.0</code> cannot connect to the Internet either so we will set <code>C1</code> to <code>15.0.0.1</code>, we do not need to change its mask so we will set <code>R22</code> IP to <code>15.0.0.254</code> and now change <code>C</code> next hop to the same IP.
  - We need to set <code>D</code> to an IP in the <code>R23</code> subnet, for example <code>73.55.47.173</code>. But in order to connect <code>D</code> to <code>C</code> (and the Internet later) we will set its target as <code>default</code> or <code>0.0.0.0/0</code>.
  - Let us go for the next goal, now <code>A</code> must connect to the Internet so we will change its routing table, setting its next hop as <code>R11</code> IP and its target as <code>default</code> or <code>0.0.0.0/0</code>. In order to get connection back from the Internet we must set its routing table to connect to our computer. Let us set the first target to <code>192.18.14.0/24</code> so it can connect to all this subnet.
  - Now <code>A</code> must connect to <code>D</code>. In order to do this we must set <code>R1</code> routing table properly. Let us set its first target to <code>D1</code> IP and set all its next hops to <code>R21</code> IP. In addition to this let us set <code>R13</code> IP to <code>50.81.18.254</code> so it can connect to <code>R21</code>. To get reverse way let us set <code>R2</code> next hop to <code>R13</code> IP.
  - Two goals left. Now <code>B</code> needs to connect to <code>C</code>. Firstly let us set its route as <code>C</code> IP and its next hop as <code>R11</code> IP.
  - Next, we need to set <code>R1</code> routing table so it can connect to <code>C</code>. In order to do this let us change its second target to <code>C1</code> IP.
  - Lastly we just need to change Internet routing table, setting its second target as <code>C1</code> IP.
  
  ![](/sol_img/Level_9.png)
 </details>
 
   <details>
  
  <summary>Exercise 10</summary>
  </br>
  This exercise seems difficult but it is quite simple, since there are only a few gaps to set.
  
  - Firstly let us set <code>R23</code> IP to <code>H4</code> next hop, and its mask to <code>H41</code> mask.
  - Let us set <code>R13</code> mask to <code>R21</code> mask.
  - Let us set <code>H21</code> and <code>H22</code> masks to <code>R11</code> mask.
  - We want all our IPs to be in <code>162.146.1.X</code> range, so let us change <code>H21</code> IP to, for example, <code>162.146.1.3</code>.
  - Now let us set <code>R22</code> and <code>H31</code> IPs to, for example, <code>162.146.1.193</code> and <code>162.146.1.194</code>. And let us set their masks to <code>/27</code> or <code>255.255.255.224</code>
  - Lastly let us set R1 routing table to <code>162.146.1.0/24</code> so it can connect to all our IPs and same for the Internet routing table
  
  ![](/sol_img/Level_10.png)
 </details>
