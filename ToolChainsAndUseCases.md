Experimental labeling of some toolchains and their use cases



# Introduction #

It is really hard to flesh out how to group these tool chains, so we decided to take the Google approach and release early and often. This is a rough draft to get some common toolchains on paper.

I think there may be several kinds of toolchains, interactive, automated, and hybrid. AKA quantitative and qualitative.

# Todo #
I think some of the charts circulated on the mailing list need deployed here. In fact I am thinking it may be a deployment upside down tunnel. As things bootstrap, they go into run time which is defined by continuous change, but no more bootstrapping. It's basically a process of Bootstrap -> Deploy -> Spawn Children.

Types of resources
  1. Infrastructure: Network/Server Hardware
  1. Platform: Load balancers, Web Servers
  1. Application: Could be many deployed on a Infrastructure/Platform resource

Processes
  1. Bootstrap: highly qualitative
  1. Deploy: highly automated

Bootstrap/Deploy Cycle
  1. Bootstrap Infrastructure -> Production Cycle Infrastructure
  1. Bootstrap Platform -> Production Cycle Platform
  1. Bootstrap Application -> Production Cycle: Application
  1. Repeat 3 until resource no longer suits needs

# Tool Chains #


## Artifact Types and Repositories ##

Rsync-ing file systems, NFS/DFS shared artifacts, Package repositories like YUM.  This decision effects your toolchain significantly

See:
  * http://groups.google.com/group/devops-toolchain/browse_thread/thread/804e3c7b6faa6fd8
  * http://groups.google.com/group/devops-toolchain/browse_thread/thread/63f1947a9661fa80

## Fully Automated Provisioning ##

The first toolchain documented

![http://controltier.org/mediawiki/images/thumb/4/4f/ProvisioningToolchain.png/800px-ProvisioningToolchain.png](http://controltier.org/mediawiki/images/thumb/4/4f/ProvisioningToolchain.png/800px-ProvisioningToolchain.png)

### Bootstrapping ###
Bootstrap of hardware to a known starting point. The development process is interactive, but the deployment side is automated.

Cobbler, xCAT, Kickstart, etc

### System Configuration ###
IP addresses, shared/local file systems, access control/firewall, printers, etc

cfengine, Chef, Puppet, etc

### Command Dispatching/Orchestration ###
Runtime network, server changes and code deployment. This would be interactive changes in configuration and application code.



## Monitoring/Instrumentation ##
The goal would be to have most of the deployment automated to a baseline, but there will always be exceptions and new technology integration. The run time should be highly automated except for acknowledgements

### Control Charting ###

Histograms of state with threshold event generation.

### Alarm Management ###
Larger tool chain that encompasses both automated and interactive tools

### Runbook Automation ###
Control Sequencing to go from out of control to in control state can be complex and can have both automated and interactive tool chains

### Analysis ###

Made up of interactive toolchains.  The production data warehouse is used by the entire enterprise!


#### Infrastructure ####
Encompasses logs from infrastructure and platform systems (eg. switches, routers, firewalls, servers, load balances)

##### Use Cases #####

Example:
```
cat /var/log/messages | grep error | petit --hgraph
```

#### Database ####
Interactive tools to analyze databases
> mysqlbinlog, maatkit

#### Platform ####
Apache, appservers, app engine, etc

#### Application ####
Often written by devs, used by webops

## Incident Management ##

See:
  * http://en.oreilly.com/velocity2008/public/schedule/detail/1525
  * http://groups.google.com/group/devops-toolchain/browse_thread/thread/9b5a22150706f082

## Change Automation and Continuous Deployment ##

  * SCM
  * Config as code
  * Testing

## Security ##
TBD