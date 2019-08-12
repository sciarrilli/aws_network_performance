# AWS Network Performance
Out of curiousity I wanted to test the networking performance of the 100Gb performance in AWS. The c5n as well as the i3en peaked my interest in seeing the bandwidth performance hit 100Gbps on my terminal. So I fired up two i3en.24xlarge in a placement group in the us-east-1. 

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