# AWS-Cross-Region-VPN #
This is a easy solution to create a VPN connection between to AWS VPC in different region.
This is a simple template that creates an instance with Openswan that will connect to an AWS VPN connection endpoint located in the other VPC.

As AWS specify in its Openswan documentation:
> Openswan configuration consists of two tunnels. Both tunnels must be configured, but only one of those tunnels should be up at any given time.

So `vpn-health-checker` is a linux service that will constantly check if the paired network is reachable or if the current tunnel is down, if it finds an issue it switches between tunnels and make vpn healthy again.

In adition `vpn-health-checker` is constantly publishing a metric to cloudwatch, so you are able to check and monitor the amount of erros the process finds and those graph makes easy to note when something anormal is happens.

![alt tag](https://github.com/clmoreno/AWS-Cross-Region-VPN/raw/master/vpn-diagram.png)
