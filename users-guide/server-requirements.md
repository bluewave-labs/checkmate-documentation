---
icon: computer
---

# Server requirements

Checkmate is an optimized monitoring solution. While it runs on modest hardware, knowing your hardware requirements is important.&#x20;

Here is an example: When you have 300 monitors, you'll need 3Gb of disk space each month if they are configured to check in 1 sec periods (intervals). This means that you'll need 36Gb of disk for the entire year to monitor 300 servers.

By default, Checkmate has a data retention policy of 90 days. This can be configured under Settings. Hence, if you need Checkmate to keep longer data periods, you can set it up accordingly.&#x20;

By default, the Checkmate uses the `snappy` MongoDB compression method, featuring CPU usage with a moderate compression ratio. This is suitable for workloads where speed is more critical than storage savings. If you want, you can always use `zlib` in MongoDB configuration, which has a higher compression ratio than `snappy` but with more CPU overhead.

