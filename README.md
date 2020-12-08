# Monitoring & Telemetry

`Learning Resources for DevOps, SRE, Cloud & Engineering Management`

[![BINPIPE](https://img.shields.io/badge/BINPIPE-YouTube-red)](https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A?sub_confirmation=1)
[![Learn DevOps!](https://img.shields.io/badge/BINPIPE-Learn--DevOps-orange)](https://github.com/BINPIPE/resources/blob/master/devops-lesson-plans.md)
[![BINPIPE](https://img.shields.io/badge/Live--Classroom-blue)](https://forms.gle/tDJxDyj2nJyfsgsk7)


**Monitoring** provides feedback from production. Monitoring delivers information about an application’s performance and usage patterns.

One goal of monitoring is to achieve high availability by minimizing time to detect and time to mitigate (TTD, TTM). In other words, as soon as performance and other issues arise, rich diagnostic data about the issues are fed back to development teams via automated monitoring. That’s TTD. DevOps teams act on the information to mitigate the issues as quickly as possible so that users are no longer affected. That’s TTM. Resolution times are measured, and teams work to improve over time. After mitigation, teams work on how to remediate problems at root cause so that they do not recur. That time is measured as TTR.

A second goal of monitoring is to enable “validated learning” by tracking usage. The core concept of validated learning is that every deployment is an opportunity to track experimental results that support or diminish the hypotheses that led to the deployment. Tracking usage and differences between versions allows teams to measure the impact of change and drive business decisions. If a hypothesis is diminished, the team can “fail fast” or “pivot”. If the hypothesis is supported, then the team can double down or “persevere”. These data-informed decisions lead to new hypotheses and prioritization of the backlog.

**Telemetry** is the mechanism for collecting data from monitoring. Telemetry can use agents that are installed in the deployment environments, an SDK that relies on markers inserted into source code, server logging, or a combination of these. Typically, telemetry will distinguish between the data pipeline optimized for real-time alerting and dashboards and higher-volume data needed for troubleshooting or usage analytics.

**Synthetic monitoring** uses a consistent set of transactions to assess performance and availability. Synthetic transactions are predictable tests that have the advantage of allowing comparison from release to release in a highly predictable manner. Real User Monitoring (RUM), on the other hand, means measurement of experience from the user’s browser, mobile device or desktop, and accounts for “last mile” conditions such as cellular networks, internet routing, and caching. Unlike synthetics, RUM typically does not provide repeatable measurement over time.

Monitoring is often used to “test in production”. A well-monitored deployment streams the data about its health and performance so that the team can spot production incidents immediately. Combined with a Continuous Deployment Release Pipeline, monitoring will detect new anomalies and allow for prompt mitigation. This allows discovery of the “unknown unknowns” in application behavior that cannot be foreseen in pre-production environments.

*Effective monitoring is essential to allow DevOps teams to deliver at speed, get feedback from production, and increase customers satisfaction, acquisition and retention.*

___

## Common Linux Monitoring Commands
Below are some common linux monitoring commands:
```
1- Top  
2- HTOP  
3- Free  
4- Telnet  
5- MyTOP  
6- IOStat  
7- SAR  
8- LSOF  
9- VMSTAT  
10- netstat
```
## Top

Top is a basic command which majority of system admins use as part of their daily job. You don’t need to install TOP as it’s already part of every Linux distribution. Following screenshot shows the result of top command. As you can see in the following screenshot running tasks , their CPU, memory and swap usage. You can do whole lot of things to get the output of your liking and need. It has a large number of options/switches which you can use to make your life easy.

`top`

## Htop

Htop is another tool just like “top” to monitor your systems processes. It comes with an interactive overview and you can kill processes by just going on them and pressing the desired button. It’s better than top because it has different mediums of showing memory and swap. You can install htop by the following command.

`yum install htop` or `apt-get install htop`

`htop`

## Free

Free also comes pre-installed with Linux distributions, to check the memory usage. It shows you buffers and cached memory as well. There are several formats like KB, MB and GB. You just have to use ‘m’ and ‘g’ parameter with the command. 

`free -m`

## Telnet

Telnet is an application protocol used on the Internet or local area network to provide a bidirectional interactive text-oriented communication facility using a virtual terminal connection. It can also be used to check open ports:

`telnet google.com 443`


## Mytop

Mytop tool allows you to monitor your systems mysql performance. It keeps refreshing itself like watch command. It opens a connection to mysql and remains in monitor state and execute the “SHOW FULL PROCESSLIST” query from time to time. Following command is used to monitor mysql database.

`mytop –u root –p XXX –d mysql`


## Iostat

Iostat command reports you the CPU and disk I/O stats. Reads and writes are shown as block read and block writes. You can get the idle percentage of your CPU to check how much time it has not done any heavy task. Following is the output of iostat command. As you can see in the following screenshot that system is 96 percent idle while sda represents you hard disk.

`iostat`


## Sar

Sar command is somehow similar to the “Iostat” command but one thing that’s different is that it tells you I/O writes for the last half hour with other parameters like system usage, i/o wait and idle time percentage. You will need to run following command to install sar command on RHEL and its derivatives.

`yum -y install sysstat` or `apt-get install sysstat`

`sysstat`

## Lsof

As you know that in Linux every process opens a file on the backend so if you want to check that a process is spawned or not, you have to check the file opened for that process in the respective partition/directory. LSOF command lets you know the files opened. For exmaple, which files are currently opened from /var partition, you will use it as:

lsof /var

## Vmstat

As the name suggests, this command is used to monitor virtual memory statistics. The best thing about this command is that it can enter monitor state on the basis of interval you have specified in the command. It lets you know the load, paging and interrupts a server is handling in that time. Following is command to monitor virtual memory after every 5 seconds.

`vmstat 5`

## Netstat

Netstat is a command-line network utility that displays network connections for Transmission Control Protocol, listening ports, routing tables, and a number of network interface and network protocol statistics. 

`netstat -tulpn`

In case this command does not work install it with:
`yum install nettools`
___

### System Monitoring with Netdata

[Netdata](https://www.netdata.cloud/)  is a system monitoring system, designed to be distributed, lightweight, flexible and open source. The source code is available for download from  [GitHub](https://github.com/netdata/netdata).

The application is able to detect hundreds of metrics automatically, simplyfing their configuration and integration. The applications core is written in C and hundreds of collectors are available to collect thousands of different metrics while being very lightweight and not requiring additional computing power. Netdata can either run autonomously, without any third-party components, or it can be integrated to existing monitoring toolchains like  [Prometheus](https://www.scaleway.com/en/docs/configure-prometheus-monitoring-with-grafana/), Graphite, OpenTSDB,  [Kafka](https://www.scaleway.com/en/docs/configure-apache-kafka/),  [Grafana](https://www.scaleway.com/en/docs/monitor-kubernetes-cluster-with-grafana/), and more.

Installing Netdata:
```
bash <(curl -Ss https://my-netdata.io/kickstart.sh)
```
Accessing Netdata:

1 . Open a web browser on your local computer, for example Chrome or Firefox.

2 . Point it to  `http://<netdata_instance_ip>:19999/`  (replace  `<netdata_instance_ip>`  with the public IP address of your instance.)

___


### Basic Docker Monitoring

Monitoring Docker, no matter if used purely or integrated into one of the systems mentioned above, should include aspects of health, performance, and resource usage of the containers. Failures in the daemon directly influence the health of the system as a whole. There are many ways to monitor basic Docker indicators.  

**Docker Stats:** The easiest tool to use and monitor Docker containers is Docker Stats, which is built into the actual Docker CLI (command line interface). Replicating much of the style known from famous Linux tools like top or iotop, it provides information about container names, CPU, memory and io (block device and network) usage.  

`docker stats`

**cAdvisor**  Runtime information together with other important metrics can be picked up with  [cAdvisor](https://github.com/google/cadvisor). cAdvisor can be launched as a docker container to monitor other docker containers. It can be launched via the following command:

```
VERSION=v0.36.0 # use the latest release version from https://github.com/google/cadvisor/releases
sudo docker run \
  --volume=/:/rootfs:ro \
  --volume=/var/run:/var/run:ro \
  --volume=/sys:/sys:ro \
  --volume=/var/lib/docker/:/var/lib/docker:ro \
  --volume=/dev/disk/:/dev/disk:ro \
  --publish=8080:8080 \
  --detach=true \
  --name=cadvisor \
  --privileged \
  --device=/dev/kmsg \
  gcr.io/cadvisor/cadvisor:$VERSION

```
cAdvisor is now running (in the background) on  `http://localhost:8080`. The setup includes directories with Docker state cAdvisor needs to observe.

___





___
:ledger: Maintainer: **[Prasanjit Singh](https://www.linkedin.com/in/prasanjit-singh)** | **www.binpipe.org**
___

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
<br><sub><sup>
[Digital Millennium Copyright Act (DMCA) Notice](https://github.com/BINPIPE/resources/blob/master/dmca.md) <br>
If you benefited from the content here consider supporting the initiative! <br>
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://paypal.me/Prasanjit?locale.x=en_GB)
</sup></sub>
