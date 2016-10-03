# Docker-HAproxy
HAProxy Load Balancer
This is a jantoniogc/docker-haproxy docker container with HAProxy load balancer. 

This container is built that any extra parameters provided to docker run will be passed directly to haproxy command. For example, if you run docker run [run options] jantoniogc/haproxy -n 1000 you pass -n 1000 to haproxy daemon.

The default haproxy.cfg is provided just for demonstration purposes, so of course you will want to override it.

Auto restart when config changes

This container comes with inotify to monitor changes in HAProxy config and reload HAProxy daemon. The reload is done in a way that no connection is lost.

ENV variables

HAPROXY_CONFIG
Default: HAPROXY_CONFIG=/etc/haproxy/haproxy.cfg
If you mount your config to different location, simply edit it.

Usage

Basic

docker run -ti -p 80:80 -p 443:443 jantoniogc/docker-haproxy

Mount custom config , override some options

docker run -d -p 80:80 -v /my-haproxy.cfg:/etc/haproxy/haproxy.cfg jantoniogc/docker-haproxy -n 10000
Note: in this case config is mounted to its default location, so you don't need to modify HAPROXY_CONFIG variable.

Stats

The default URL for stats is http://CONTAINER_IP/admin?stats with username:password ser to auth:auth.

[https://images.microbadger.com/badges/image/jantoniogc/docker-haproxy.svg](https://microbadger.com/images/jantoniogc/docker-haproxy "Get your own image badge on microbadger.com")

Authors

Author: Juan Antonio González Cano
