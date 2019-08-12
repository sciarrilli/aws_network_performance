# AWS Network Performance
Out of curiousity I wanted to test the networking performance of the 100Gb performance in AWS. The c5n as well as the i3en peaked my interest in seeing the bandwidth performance hit 100Gbps on my terminal. So I fired up two i3en.24xlarge in a placement group in the us-east-1. Then I installed iperf3 on both instances. I had to background the processes of iperf and run it multiple times on the server and the client to actually generate multiple flows. 

# Performance in a Region
What I observed in a region and inside of a placement group with the i3en.24xlarge is that a single flow receives 25Gb of bandwidth. I then backgrounded the iperf processes and started to add additional iperf sessions. Each additional session would increment the traffic by almost 25Gb. As I added more and more iperf sessions the added bandwidth would diminish as I approached 100Gbps. The sweet spot seems to be 7 iperf sessions which maxed out the bandwidth at 91 Gbps. 



```
iperf3 -s -p &
iperf3 -s -p 5202 &
iperf3 -s -p 5203 &
iperf3 -s -p 5204 &
iperf3 -s -p 5205 &
iperf3 -s -p 5206 &
iperf3 -s -p 5207 &
iperf3 -s -p 5208 &
iperf3 -s -p 5209 &
iperf3 -s -p 5210 &
```


```
iperf3 -c 172.31.90.102 -P 96 -t 600 &
iperf3 -c 172.31.90.102 -P 96 -t 600 -p 5202 &
iperf3 -c 172.31.90.102 -P 96 -t 600 -p 5203 &
iperf3 -c 172.31.90.102 -P 96 -t 600 -p 5204 &
iperf3 -c 172.31.90.102 -P 96 -t 600 -p 5205 &
iperf3 -c 172.31.90.102 -P 96 -t 600 -p 5206 &
iperf3 -c 172.31.90.102 -P 96 -t 600 -p 5207 &
```

```
iperf3 -c 100.64.3.38 -P 96 -t 600 &
iperf3 -c 100.64.3.38 -P 96 -t 600 -p 5202 &
iperf3 -c 100.64.3.38 -P 96 -t 600 -p 5203 &
iperf3 -c 100.64.3.38 -P 96 -t 600 -p 5204 &
iperf3 -c 100.64.3.38 -P 96 -t 600 -p 5205 &
iperf3 -c 100.64.3.38 -P 96 -t 600 -p 5206 &
iperf3 -c 100.64.3.38 -P 96 -t 600 -p 5207 &
iperf3 -c 100.64.3.38 -P 96 -t 600 -p 5208 &
iperf3 -c 100.64.3.38 -P 96 -t 600 -p 5209 &
iperf3 -c 100.64.3.38 -P 96 -t 600 -p 5210 &
```