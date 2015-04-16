# Motivation #

It is often desirable to upgrade a software deployment without losing any changes to files that are relied upon when the software is in operation. For example, running software produces data written to files that might store software state, log messages, or business transaction information. For the software to operate correctly, a number of configuration settings stored in files will also be found. If these deployment specific files are not identified, they may be lost or damaged during the software update process. Further complicating the upgrade process is the practice of mixing executable and data files inside the same directory structure. This creates an obscure picture that makes it difficult to understand the impact of later software releases. Finally, support staff benefit from having visibility into locations of log and configuration data so they can look up and read them for monitoring and troubleshooting.

If the software deployment resides under one directory, one might support the update process by backing up the entire software directory hierarchy before copying in files from the next release. This approach might not be practical if the number and or size of files is too great. This approach is problematic if the software files are spread across the file system. In another approach each edition of software is located in its own directory structure. This avoids the chance of files being lost or damaged but breaks data continuity for the running software state. Often times, this continuity is made necessary by the software and or the support staff that operates the environment.

A more flexible approach is to separate the executable software files that change between releases from the deployment-specific ones to avoid data loss or damage and preserves data continuity. Using this approach executable software files are placed in one directory hierarchy while the data files are placed in another.
The process to achieve the code/data split is done over several steps. First, an installation of the software is created and then brought into running operation. Second, the data files created by the running software are identified, along with configuration files that must be changed to support the new software instance. Move the identified files into their own directory hierarchy. Finally, reconfigure the software instance to refer to the new location. This running software instance now represents the new reference installation of the "split". The release process is then modified to package only the executable files and the deployment process is modified to preserve the files in the data directory.

# Applicability #

Use this pattern:

  * when you need data continuity. This preserve data files produced or modified during deployment and operation.
  * to manage key configuration files that need to be maintained separately from the software releases.
  * as a first step in running multiple instances of the same software using one set of binaries.

# Structure #

Typical directory structure showing the split:
<pre>
rootdir<br>
|<br>
+- executables directory<br>
|<br>
`- data directory<br>
</pre>

# Consequences #

  * Separating software code from its data is the first step in supporting multiple deployments that share the same package images on the same computer.
  * Configuration can now be packaged separately from its software.

# Implementation #

These issues should be considered when applying the pattern:
  * Hard coded paths. Unfortunately, some software uses hard coded file paths which make this pattern very difficult to implement.


# Known Uses #

Examples of this pattern exist in operating systems and platform software. Unix established a filesystem hierarchy standard organizing binaries into "bin" directories (eg, /bin, /usr/bin, /sbin), kept host configuration separated into "etc" (eg, /etc) and variable data files under "var" (eg /var). This practice supported security by assigning different ownerships and read-write privileges.
Platform software such as web (eg, Apache), application (eg Tomcat) and database (eg Mysql) server software also support the paradigm of splitting code from data. Many of these platforms use the notion of product home versus product base directories. For example, Tomcat refers to the executables directory hierarchy as CATALINA\_HOME while the deployment specific files can be located under CATALINA\_BASE.

# Related Patterns #

  * [AdaptiveDeployment](AdaptiveDeployment.md)
  * [Monolith](Service.md): The application of the CodeData Split pattern can be used to counter the problems described [ServiceMonolith](ServiceMonolith.md) anti-pattern.