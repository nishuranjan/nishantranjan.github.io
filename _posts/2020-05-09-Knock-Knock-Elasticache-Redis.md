---
layout: post
title: Knock knock ... Elasticache Redis
---

Let's play with Elasticache Redis in AWS...

- SSH your EC2 instance (Ubuntu 18.04)

- Install redis-cli using command sudo apt install redis-tools

- Verify the correct redis endpoint.

'elasticache redis endpoint' and port 6379

- Go to redis-cli on the above redis endpoint. In our case it is like

redis-cli -c -h 'elasticache redis endpoint' -p 6379

- To see the specific key (pattern) we can go like

redis-cli -c -h 'elasticache redis endpoint' -p 6379 --scan --pattern '*hello*'

- Once run the step 5, you can see the output mentioned below:

:1:hellofriends

- If you want to see all the keys available in the redis endpoint, then go with the below command:

nranjan@ip-xxx-xx-xxx-79:~$ redis-cli -c -h 'elasticache redis endpoint' -p 6379
'elasticache redis endpoint':6379> keys *
- ":1:hellofriends"

## Other than above if want to see what's happening with memory usage, clients connected, and so forth, go with the below command:

redis-cli -c -h 'elasticache redis endpoint' -p 6379 --stat

## If you want to print all the commands received by a Redis instance, go with the below command:

redis-cli -c -h 'elasticache redis endpoint' -p 6379 monitor

Last but not the least.

## To monitoring the latency of Redis instances, go with the below command:

redis-cli -c -h 'elasticache redis endpoint' -p 6379 --latency

- The --latency-history option is used for that purpose: it works exactly like --latency, but every 15 seconds (by default) a new sampling session is started from scratch

redis-cli -c -h 'elasticache redis endpoint' -p 6379 --latency-history