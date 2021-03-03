# Blog - 01
> ## 03/03/2021
## Subnetting woes

I previously thought I had a grasp on subnetting, but after continuously getting the wrong answers on ALL the in class examples I realized I might need to pay some extra attention to it. So here are some notes that I can reference in the future. I found a method that helped me understand online, will need to check with Lars that its acceptable to use...

## Subnet
> A subnet is the logical division of an IP network, its the process of dividing it into two or more sub-networks.

> The main benefits of subnetting are to relieve network congestion. improve network performance, and increase security. 

> In order to subnet we must be able to identify subnet mask, network ID, host ID, and broadcast ID.
 
## Example
- network ID 192.168.4.0/24
- create three subnets
- define:
> 1. network ID
> 2. subnet mask
> 3. Host ID range
> 4. number of usable host IDs
> 5. broadcast ID
> 

### Solution
### 1. create subnet key table
|             	|     	|     	|     	|     	|     	|     	|     	|     	|     	|
|-------------	|-----	|-----	|-----	|-----	|-----	|-----	|-----	|-----	|-----	|
| subnet      	| 1   	| 2   	| 4   	| 8   	| 16  	| 32  	| 64  	| 128 	| 256 	|
| host        	| 256 	| 128 	| 64  	| 32  	| 16  	| 8   	| 4   	| 2   	| 1   	|
| subnet mask 	| /24 	| /25 	| /26 	| /27 	| /28 	| /29 	| /30 	| /31 	| /31 	|

> since we need three subnets, we will use :triangular_flag_on_post: 4 :triangular_flag_on_post: because `3 > 2 && 3 < 4` .

> the numbers in this column can be used to find the subnet information we need. 

|             	|     	|     	|     	|     	|     	|     	|     	|     	|     	|
|-------------	|-----	|-----	|-----	|-----	|-----	|-----	|-----	|-----	|-----	|
| subnet      	| 1   	| 2   	|:triangular_flag_on_post: 4   :triangular_flag_on_post:	| 8   	| 16  	| 32  	| 64  	| 128 	| 256 	|
| host        	| 256 	| 128 	|:triangular_flag_on_post: 64  :triangular_flag_on_post:	| 32  	| 16  	| 8   	| 4   	| 2   	| 1   	|
| subnet mask 	| /24 	| /25 	|:triangular_flag_on_post: /26 :triangular_flag_on_post:	| /27 	| /28 	| /29 	| /30 	| /31 	| /31 	|

### 2. create subnet answer table using key table values

> use the original network ID for the first, then the next network ID can be found by adding :triangular_flag_on_post: 64 :triangular_flag_on_post: 

> `0 + 64 = 64`, `64 + 64 = 128`, ...
 
> subnet mask is :triangular_flag_on_post: /26 :triangular_flag_on_post:

> the number of usable hosts is :triangular_flag_on_post: 64 :triangular_flag_on_post: minus two (netowrk ID & broadcast ID)

> the first broadcast ID is the following network ID minus one. after the first broadcast ID, add :triangular_flag_on_post: 64 :triangular_flag_on_post: to find each additional broadcast ID

> host ID range is found between the network ID and broadcast ID

| network ID    	| subnet mask 	| host ID range                 	| # of usable hosts 	| broadcast ID  	|
|---------------	|-------------	|-------------------------------	|-------------------	|---------------	|
| 192.168.4.0   	| /26         	| 192.168.4.1 - 192.168.4.62    	| 62                	| 192.168.4.63  	|
| 192.168.4.64  	| /26         	| 192.168.4.65 - 192.168.4.126  	| 62                	| 192.168.4.127 	|
| 192.168.4.128 	| /26         	| 192.168.4.129 - 192.168.4.190 	| 62                	| 192.168.4.191 	|
| 192.168.4.192 	| /26         	| 192.168.4.193 - 192.168.4.254 	| 62                	| 192.168.4.255 	|
