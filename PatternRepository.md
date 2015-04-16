This page contains a set of design patterns and anti patterns meant to capture good and bad practice. Design patterns are a useful format to some. To others, their use is an anti-pattern in itself. Either way, let the [devops-toolchain@googlegroups.com Group] know.

Note, some have commented that the language used in the descriptions sounds like [marketing gobbledygook](http://twitter.com/markimbriaco/status/10900089029) so maybe the language used here could be better phrased.

# Introduction #

First published in this [dev2ops blog post](http://dev2ops.org/blog/2010/2/18/deployment-management-design-patterns-for-devops.html), this page contains a catalog of notional design patterns. Some of them have been documented more fully while others have a brief description. Readers of Nygard's [Release It!: Design and Deploy Production-Ready Software](http://www.pragprog.com/titles/mnee/release-it) will recognize the approach here.

![http://devops-toolchain.googlecode.com/svn/wiki/images/pagoda.png](http://devops-toolchain.googlecode.com/svn/wiki/images/pagoda.png)

# Design Patterns #
<table>
<tbody>
<tr>
<th>Name</th> <th>Description</th> <th>Mitigates</th><th>Alternative names</th>
</tr>
<tr>
<td><a href='CommandDispatcher.md'>CommandDispatcher</a></td>
<td>A mechanism used to lookup and execute logically organized named procedures within a data context permitting environment abstraction within the implementations.</td>
<td><a href='TooManyTools.md'>TooManyTools</a></td>
<td>Command Framework</td>
</tr>
<tr>
<td><a href='Lifecycle.md'>Lifecycle</a></td>
<td>A formalized series of operational stages through which resources comprising application software systems must pass.</td>
<td><a href='ControlHairball.md'>ControlHairball</a></td>
<td></td>
</tr>
<tr>
<td><a href='Orchestrator.md'>Orchestrator</a></td>
<td>Encapsulates a multi-step activity that spans a set of administrative steps and or other process workflows.</td>
<td><a href='ControlHairball.md'>ControlHairball</a>, <a href='TooManyCooks.md'>TooManyCooks</a></td>
<td>Process Workflow, Control Mediator</td>
</tr>
<tr>
<td><a href='ComposableService.md'>ComposableService</a></td>
<td>A set of independent deployments that can assembled together to support new patterns of integrated software systems.</td>
<td><a href='ServiceMonolith.md'>ServiceMonolith</a></td>
<td>Composable Deployments</td>
</tr>
<tr>
<td><a href='AdaptiveDeployment.md'>AdaptiveDeployment</a></td>
<td>Practice of using an environment-independent abstraction along with a set of template-based automation, that customizes software and configuration at deployment time.</td>
<td><a href='ControlHairball.md'>ControlHairball</a>, <a href='ConfigurationBirdNest.md'>ConfigurationBirdNest</a>, <a href='UnmetIntegration.md'>UnmetIntegration</a></td>
<td>Environment Adaptation</td>
</tr>
<tr>
<td><a href='CodeDataSplit.md'>CodeDataSplit</a></td>
<td>Practice of separating the executable files (the product) away from the environment-specific deployment files, such as configuration and data files that facilitates product upgrade and co-resident deployments.</td>
<td><a href='ServiceMonolith.md'>ServiceMonolith</a></td>
<td>Software-Instance Split</td>
</tr>
<tr>
<td>PackagedArtifact</td>
<td>A structured archive of files used for distributing any software release during the deployment process.</td>
<td><a href='AdhocRelease.md'>AdhocRelease</a></td>
<td></td>
</tr>
</tbody>
</table>

# Anti Patterns #

<p>The anti-patterns might be more interesting since they represent practices that have definite disadvantages:</p>
<table>
<tbody>
<tr>
<th>Name</th> <th>Description</th> <th>Mitigated by</th><th>Alternative names</th>
</tr>
<tr>
<td><a href='TooManyTools.md'>TooManyTools</a></td>
<td>Each technology and process activity needs its own tool, resulting in a multitude of syntaxes and semantics that must each be understood by the operator, and makes automation across them difficult to achieve.</td>
<td><a href='CommandDispatcher.md'>CommandDispatcher</a></td>
<td>Tool Mishmash, Heterogeneous interfaces</td>
</tr>
<tr>
<td><a href='TooManyCooks.md'>TooManyCooks</a></td>
<td>A common infrastructure must be maintained by various disciplines but each use their own tools to affect change increasing chances for conflicts and overall negative effects.</td>
<td><a href='Orchestrator.md'>Orchestrator</a></td>
<td>Unmediated Action</td>
</tr>
<tr>
<td><a href='ControlHairball.md'>ControlHairball</a></td>
<td>A process that spans activities that occur across various tools and locations in the network, is implemented in a single piece of code for convenience but turns out to be very inflexible, opaque and hard to maintain and modify.</td>
<td><a href='Orchestrator.md'>Orchestrator</a>, <a href='AdaptiveDeployment.md'>AdaptiveDeployment</a></td>
<td></td>
</tr>
<tr>
<td><a href='ConfigurationBirdNest.md'>ConfigurationBirdNest</a></td>
<td>A network of circuitous indirections used to manage configuration and seem to intertwine like a labyrinth of straw in a bird nest. People often construct a bird nest in order to provide a consistent location for an external dependency.</td>
<td><a href='AdaptiveDeployment.md'>AdaptiveDeployment</a></td>
<td></td>
</tr>
<tr>
<td><a href='ServiceMonolith.md'>ServiceMonolith</a></td>
<td>Complex integrated software systems end up being maintained as a single opaque mass with no-one understanding entirely how it was put together, or what elements it is comprised, and how they interact.</td>
<td><a href='CodeDataSplit.md'>CodeDataSplit</a>, <a href='ComposableService.md'>ComposableService</a></td>
<td>House Of Cards, Monolithic Environment</td>
</tr>
<tr>
<td><a href='AdhocRelease.md'>AdhocRelease</a></td>
<td>The lack of standard practice and distribution mechanisms for releasing application changes.</td>
<td><a href='PackagedArtifact.md'>PackagedArtifact</a></td>
<td></td>
</tr>
</tbody>
</table>