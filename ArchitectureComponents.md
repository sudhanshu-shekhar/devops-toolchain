The goal for this page is to document hypothetical architecture that supports [BestPractices](BestPractices.md) and compare it against a set of real world examples. Having a long term architectural vision helps set the scope of what you might want to build.
Of course, there are many approaches that can be taken by those building automated infrastructure, as well as, how one manages a staged evolution of the architecture, too. For this reason, you are encouraged to share your own designs in the [Examples](#Examples.md) section below. It will be interesting to compare them to the strawman "reference" architecture and drive refinement in seeking a generic design.



# Components #
Set of functional components comprising a generic architecture. Depending on the implementation some of these roles may be supported by one or more [tools](Tooling.md).

<a href='http://devops-toolchain.googlecode.com/svn/wiki/images/architecture-components.png'><img src='http://devops-toolchain.googlecode.com/svn/wiki/images/architecture-components.png' align='right' alt='Strawman reference architectural model diagram' width='300' /></a>



## Version Control ##
Contains all tool chain related source files used to support setting up and operating the deployments and infrastructure.

## Operating system install ##
Provides operating system life cycle management including network boot, OS image installation and execution of finish scripts. May also support OS patching. The finish scripts may call out to configuration management or other administrative tools to complete the installation.

## Host naming services ##
Provides IP address to hostname mapping as a centralized service (i.e., DNS).

## Inventory ##
A database containing information about infrastructure, components, their details and interrelationships.
Sometimes referred to as a CMDB.

## Monitoring ##
Continuous status checking of vital components in the infrastructure.

## Reporting ##
Accepts and logs management events later used for historical auditing and trending.

## Email ##
Functioning SMTP service and configuration.

## Configuration management ##
Defines configuration rules for deployments and infrastructure and capable of checking compliance and enforcing the specification..

## Issue tracker ##
Manages change requests and their resolution.

## Identity management ##
Defines users, their roles as well as authorized actions.

## Deployment ##
Defines a set of deployments residing on the infrastructure as well as drive their life cycle.

## Orchestration ##
Coordinates multi-step process across a distributed environment.

## Command Dispatcher ##
Provides network abstracted remote command execution on hosts.

## Artifact repository ##
Stores packaged artifacts used to distribute throughout the infrastructure.

## Model ##
Definition of the environment, its components and their relationships. The model provides a common abstraction across the set of architectural components and can be use to drive automated processes.

# Examples #

Post your own examples here. If you are uncomfortable mentioning the company you work for, just make a broad description of the kind of environment you work in to show it might relate to another reader.

## Network Instruments ##

![http://devops-toolchain.googlecode.com/svn/wiki/images/ni-architecture-components.png](http://devops-toolchain.googlecode.com/svn/wiki/images/ni-architecture-components.png)