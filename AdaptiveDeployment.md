# Motivation #

Software components must work in a variety of host environments and application contexts throughout the application life cycle. In each location the component is deployed, a number of customizations are applied to configure the component to work in that context. The kinds of customizations include: network settings (listen ports and addresses),  host resources (paths, accounts, IPC), release specific application settings, and external dependencies (outbound ports and addresses). If these variations are not managed consistently, they will be the cause of both functional and performance problems that may be difficult to diagnose and correct. Furthermore, these variations also become an obstacle to automating release and administrative process, often requiring complicated specialized heuristics in higher level scripts.

A preferable solution would be to identify and then externalize these deployment-specific differences and then incorporate a process of adaptation that allows the software to be setup for correct operation in its target environment. An adaptive deployment is an object that models and governs the process of modifying the software during installation and make it ready for use and administration. Adaptive Deployment represents an inversion of control model where the concern being inverted is the process of obtaining the needed deployment context information along with a set of files and or logic to produce a working configuration for the software component in that location.

For example, suppose we have an Apache web server that uses plugin modules to handle SSL client connection and one to connect to a back end Tomcat server. Also, suppose the Apache server must bind to different listening ports and addresses and specify different virtual host definitions depending on the network the web server resides. In this example, two kinds of files will need modification, the httpd.conf configuration file where the SSL, virtual hosts and webapp redirection are defined and the workers.properties file where the Tomcat connector detail is specified. Using the Adaptive Deployment pattern, environment specific httpd.conf and workers.properties files will be obtained and put in place during the adaptation process. There are roughly two methods to handle the file adaptation: template-based and non-template based:

  * Using the template-based approach, configuration files are abstracted into generalized templates by replacing the environment specific values with substitution tokens. These tokens refer to a map of named values used during the token substitution process. This mapping of tokens to values represents the externalized deployment specific configuration data, which itself can now be managed separately.  Using the template-based approach, adaptation is accomplished by reading in the map of environment configuration data and file templates and generating working files. One set of generalized configuration templates are used for any deployment. For the Apache example a map of configuration data would include keys referring to the ports, addresses, and domains and there would be two template files that refer to them (eg, httpd.conf.template and workers.properties.template).

  * The non-template based approach, manages sets of pre-defined configuration files, with one file set for each environment the software will be deployed. With this approach adaption occurs by locating the appropriate set of files for the environment and copying them to the correct locations. This approach is usually accomplished by creating multiple copies of a reference set of files, modifying them to have environment-specifc values.

One can also externalize the adaption logic itself by having environment-specific code looked up and applied. In this mode the adaption process is really just a framework that simply mediates the process invoking the external adaption logic, passing it control of the process at the time of deployment.

# Applicability #

Use the Adaptive Deployment pattern when:

  * you want to generalize the deployment process for a software component.
  * there is a need to manage configuration data and files independent of software release and environment context.
  * as a first step towards composing services comprised integrated software by assembling other adaptive deployments.

# Structure #

  * Adaptive Deployment
  * Configuration model
  * Configuration templates

# Consequences #

The Adaptive Deployment pattern offers the following benefits:

  * Increases flexibility of deployment
  * Improves visibility and management of integration configuration data.
  * Externalizes the variation into its own component and process

# Implementation #

Consider the following issues when implementing an Adaptive Deployment:

  1. a harness: Something must govern the adaptation process, be it a package install tool, underlying software platform, or a management framework.
  1. model: In its most simple form, a map of environment details can be a table of key value pairs stored in a file. More sophisticated forms might describe a schema of allowed data types and pertinent metadata.
  1. templates vs prepared files: The advantage to using templates rather than prepared files is they reduce maintenance overhead by just having one set of files produce environment specific ones. This makes the process purely data driven. This works well if there are just difference in values but gets more complicated if the content and structure differs from environment to environment. Various template languages exist (eg XSL, Perl template toolkit, etc.) that allow for conditional logic, iteration and other programming structures.

# Known Uses #

Application frameworks like Spring (and other dependency injection systems) promote the practice of externalizing configuration into its own files to wire together components at deployment time.

# Related Patterns #

Related design patterns:
  * CodeDataSplit: The process of establishing an adaptive deployment is facilitated by the CodeData Split pattern since one of its first steps is the identification of files that are changed during installation. Adaptive Deployment takes the notion of CodeDataSplit one step further by externalizing the deployment-specific configuration differences and managing them as a separate process.

Related anti-patterns:
  * ConfigurationBird-nest: counters it
Without adaption, software could only be made to work in one place. The more adaptive software is the greater its fitness to work in any context.
  * ControlHairball: Avoids complicated specialized heuristics in large monolithic scripts.