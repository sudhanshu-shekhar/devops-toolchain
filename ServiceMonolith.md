# Problem #

A business service based on a multi-component software system is updated with releases at different times for each of its deployments. Each component has its own method for release, and none of them very formalized. Also, component integrations are done via application configurations that are also maintained individually, and often manually.

# Context #

Organizations that operate software as a service.

# Forces #

Multiple concurrent development streams. Deadlines and short time frames late in the release cycle.

# Supposed Solution #

Use a surgical approach to maintain the working system by attempting to precisely modify individual components by hand, "in situ".  This avoids disturbing the rest of the components, (presumably) limiting the scope of impact.

# Resulting Context #

A brittle  system that is hard to maintain and might be described as a "house of cards" . Reproducing the service in another environment is extremely time consuming and difficult since the assembly process must be rediscovered each time. The result is often an aversion to change, and hence, makes the software system and its environment an intractable mass, or monolith. A typical consequence is to isolate services from one another, requiring dedicated infrastructure for each place the service is required (i.e., silos).

# Design Rationale #

Because it would be too complicated or would take too much time to implement a method that reproduces the entire environment from a repeatable and automated process. It is better to change things in place when time is short, even if it frequently happens.

# Related Anti-Patterns #

caused by: Adhoc Release, Configuration Bird-nest
leads to: Control Hairball

# Applicable Positive Patterns #

CodeDataSplit, ComposableService, [PackagedArtifact](PackagedArtifact.md)