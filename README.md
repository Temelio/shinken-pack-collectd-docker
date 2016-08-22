# shinken-pack-collectd-docker

## Description

This Shinken monitoring pack is used to manage docker services with our
standard deployment of Collectd.

We request Collectd data using unixsock plugin and collectd-nagios script from
collecd-utils package.

This pack depends to shinken-pack-collectd-base to work

## Objects

### Templates

#### Host templates

* collectd-docker: Manage all default thresholds and values for services

### Services

| Service name             | Description             | Value specification                            | DS        | Consolidation | Warning variable | Critical variable | Duplicate_foreach variable |
|--------------------------|-------------------------|------------------------------------------------|-----------|---------------|------------------|-------------------|----------------------------|
| Docker - $KEY$ processes | Check Docker processes  | processes-$VALUE1$/ps_count                    | processes | none          | $VALUE2$         | $VALUE3$          | _docker_processes          |
| Docker - $KEY$           | Check listening ports   | tcpconns-$VALUE1$-local/tcp_connections-LISTEN | value     | none          | $VALUE2$         | $VALUE3$          | _docker_listen             |

## Default values

    _docker_processes   docker $(docker)$$(1:1)$$(1:1)$
    _docker_listen      Listen 2375 $(2375)$$(1:1)$$(1:1)$
