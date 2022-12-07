# Basic check for linux performance


This video is taken from [this blog post](https://www.brendangregg.com/blog/2015-12-03/linux-perf-60s-video.html).

<iframe width="560" height="315" src="https://www.youtube.com/embed/ZdVpKx6Wmc8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


In short:

```bash
uptime \
dmesg | tail \
vmstat 1 \
mpstat -P ALL 1 \
pidstat 1 \
iostat -xz 1 \
free -m \
sar -n DEV 1 \
sar -n TCP,ETCP 1 \
top
```

