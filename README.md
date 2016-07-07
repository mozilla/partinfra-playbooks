# Participation Infrastructure
## Ansible Playbooks
### Introduction

``partinfra-playbooks`` is a collection of Ansible playbooks to manage the infrastructure that powers various sites related to mozilla community. The code in this repository is authored and maintained by Mozilla engineers and a vibrant community of volunteer contributors.

For more information:

* [Community Ops overview](https://wiki.mozilla.org/Community_Ops)
* [Community Ops PaaS architecture](https://wiki.mozilla.org/Community_Ops/paas)
* [Ansible documentation](https://docs.ansible.com/ansible/index.html)
* Communication:
  *  IRC: ``#communityit`` on irc.mozilla.org
  *  Discourse: ``https://discourse.mozilla-community.org/c/community-ops``

Get Involved!

### Roles

* Common
* Consul
  * Configures our [Consul](https://www.consul.io/) cluster used for service discovery and distributed key-value storage.
  * [Consul](https://www.consul.io/) is also used to autoconfigure various templates using [consul-template](https://github.com/hashicorp/consul-template)
* Jenkins
* Mesos
  * ``mesos-common``
  * ``mesos-master``
     * Configures the master nodes of our mesos cluster
         * [Zookeeper](https://zookeeper.apache.org/) for leader election
         * [Mesos master](https://open.mesosphere.com/reference/mesos-master/) for cluster resource management
         * [Marathon](https://mesosphere.github.io/marathon/) for container orchestration
  * ``mesos-slave``
     * Configures the slave nodes of our mesos cluster
         * Configures [docker](https://www.docker.com/) in all container hosts
         * Configures [mesos slave](https://open.mesosphere.com/reference/mesos-slave/) that manages resource offers and task launching
* OpenVPN
  * ``openvpn-firewall``
     * Configures ``iptables`` rules for our VPN traffic.
* Storage
  * Configures our [GlusterFS](https://www.gluster.org/) cluster.
  * Provides a distributed and scalable storage solution.
  * We mainly use it as persistent storage backing our docker instances.

### Ansible galaxy dependencies

* [Stouts.OpenVPN](https://galaxy.ansible.com/Stouts/openvpn/)
* [tersmitten.postfix](https://galaxy.ansible.com/tersmitten/postfix/)
* [jnv.unattended-upgrades](https://galaxy.ansible.com/jnv/unattended-upgrades/)

### Issues

For issue tracking we use bugzilla.mozilla.org. [Create a bug][1] on bugzilla.mozilla.org under ``Participation Infrastructure > Community Ops`` component.

[1]: https://bugzilla.mozilla.org/enter_bug.cgi?product=Participation%20Infrastructure&component=Community%20Ops
