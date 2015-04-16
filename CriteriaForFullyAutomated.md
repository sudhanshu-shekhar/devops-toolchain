# Introduction #

“Fully automated provisioning” means having the ability to deploy, update, and repair your application infrastructure using only pre-deﬁned automated procedures. While this might seem like a straightforward concept, the details of what it really means are often still open for interpretation during automation implementations.

Like most endeavors, fully automated provisioning needs a target. When we say "fully automated" is should mean something specific. Below is a list of criteria that attempts to define what "fully automated" means when it comes to provisioning.

(the foundation for this list comes from the ["WebOps 2.0: Achieving Fully Automated Provisioning"](http://dev2ops.org/toolchain/) whitepaper).


# Criteria for Fully Automated Provisioning #

**1. Be able to automatically provision an entire environment -- from "bare-metal" to
running business services -- completely from speciﬁcation**

Starting with bare metal (or stock virtual machine images), can you provide a
speciﬁcation to your provisioning tools and the tools will in turn automatically
deploy, conﬁgure, and startup your entire system and application stack? This means
not leaving runtime decisions or "hand-tweaking" for the operator. The speciﬁcation
may vary from release to release or be broken down into individual parts provided to
speciﬁc tools, but the calls to the tools and the automation itself should not vary
from release to release (barring a signiﬁcant architectural change).


**2. No direct management of individual boxes**

This is as much a cultural change as it is a question of tooling. Access to individual
machines for purposes other than diagnostics or performance analysis should be
highly frowned upon and strictly controlled. All deployments, updates, and ﬁxes
must be deployed only through speciﬁcation-driven provisioning tools that in turn
manages each individual server to achieve the desired result.


**3. Be able to revert to a "previously known good" state at any time**

Many web operations lack the capability to rollback to a "previously known good"
state. Once an upgrade process has begun, they are forced to push forward and
ﬁreﬁght until they reach a functionally acceptable state. With fully automated
provisioning you should be able to supply your provisioning system with a previously
known good speciﬁcation that will automatically return your applications to a
functionally acceptable state. The most successful rollback strategy is what can be
described as "rolling forward to a previous version”. Database issues are generally
the primary complication with any rollback strategy, but it is rare to ﬁnd a situation
where a workable strategy can't be achieved.


**4. It’s easier to re-provision than it is to repair**

This is a litmus test. If your automation is implemented correctly, you will ﬁnd it is
easier to re-provision your applications than it is to attempt to repair them in place.
“Re-provisioning” could simply mean an automated cycle of validating and
regenerating application and system conﬁgurations or it could mean a full
provisioning cycle from the base OS up to running business applications.


**5. Anyone on your team with minimal domain speciﬁc knowledge can deploy or update
an environment**

You don't always want your most junior staff to be handling provisioning, but with a
full automated provisioning system they should be able to do just that. Once your
domain speciﬁc experts collaborate on the speciﬁcation for that release, anyone
familiar with a few basic commands (and having the correct security permissions)
should be able to deploy that release to any integrated development, test, or
production environment.