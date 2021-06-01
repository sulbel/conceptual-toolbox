# Puppet

## Infrastructure as Code
* Clicking through GUI screens to spin up new VMs can be time consuming
* This led to tools like Terraform, Vagrant being introduced to automatically provision new servers in the cloud by means of writing configuration code (IaC)
  * Tools like Ansible, Chef, Puppet allow us to automate the configuration and maintanence of these servers
* Particularly useful for scaling out e.g. when the application traffic explodes and the need for new load balancers/application servers arises

## Why Puppet?
* Domain specific language that is easy to learn
* Surprisingly robust
* DSL is mostly declarative

## Resource Abstraction Layer
* Wish to configure a webserver
  * Install the **package**
  * Change some config **file** settings
  * Start the **service**
* The RAL abstracts system resources to puppet resources

## Puppet Architecture
* Master runs a **server service**
  * Each master can handle 1000+ client agents
* Slaves run an **agent service**
  * Agent service initiates a *catalog request* from the master at regular intervals (30 minutes by default)

## Prepping a "base" VM
* To-do list:
  * Configure the Puppet repo
  * Add 'puppet' to path
  * Install NTP
  * Include puppet *master* IP in 'hosts' file
  * Install the Linux development libraries
* Setting a CentOS IP address:
```
nmcli c mod <ens32> ipv4.method manual \
                    ipv4.addr "10.10.10.101/24" \
                    ipv4.dns 10.10.10.2 \
                    gw4 10.10.10.2

nmcli c up <ens32>
```
* Setting a hostname:
`hostnamectl set-hostname puppet.host.name`

* Enabling the `NTP` service: `systemctl enable --now ntpd`

* Punching holes in the firewall: `firewall-cmd --add-port=5432/tcp --perm`


## Manifests and Classes

### Manifests
* A simple resource, in a file named `greeting.pp`:
```
notify {'Course':
  message => 'Getting started with Puppet',
}
```
* Check if code is free of syntax errors with `puppet parser validate <path/to/file>`
* Run the Manifest with `puppet apply <path/to/file>`
