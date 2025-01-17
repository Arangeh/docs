## Apache Maven
- Has a three built-in biuld lifecycles 
	- default
	- clean
	- site
- each life-cycle comprises sequence of phases.
- for example default build lifecycle phases:
	- validate
	- compile
	- test
	- package
	- verify
	- install
	- deploy
- each phase bundled with zero or more goals
- in maven goal is a smallest unit of work
- each goal belong to one plugin which illustrated as bellow
```
plugin:goal
e.g.
mvn help:effective-pom
mvn clean dependency:copy-dependencies
``` 
### POM
##### POM stands for "Project Object Model" .It is an XML representation of a `Maven project` held in a file named *pom.xml* .It is an XML file that contains information about the project and configuration details used by Maven to build the project. like OOP , pom files support inheritance . the parent of all pom files is `super-pom` which has a default configurations .
>*maven project* could be a single pom.xml file without any other file
> e.g parent-pom that has a packaging type *pom*


> Each packaging ( "jar","war","ear","pom" )  contains a list of goals to bind to a particular phase.
> For example A project that is purely metadata (packaging value is pom) only binds goals to the `install` and `deploy` phases 

- super-pom
	- The Super POM is Maven's default POM. All POMs extend the Super POM unless explicitly set, meaning the 	   configuration specified in the Super POM is inherited by the POMs you created for your projects.
- effective-pom
	- The pom used for build (POM that results from the application of interpolation, inheritance and active 	   profiles) a project .
- parent-pom
	- A pom which other poms can inherit its ( dependencies , properties , goal bindings )
- aggregate-pom
	- cascade your maven commands to its modules

### Plugin
- add goals to phases
##### plugins can contain information that indicates which lifecycle phase to bind a goal to. Note that adding the plugin on its own is not enough information - you must also specify the goals you want to run as part of your build.

## Maven dependency management
- maven project classpath libs(dependencies) management
- in maven project we have  **`transitive dependency`** and **`direct dependency`** .
- both kind of dependencies will be in a maven project classpath libs .
- **transitive dependency** is a dependency of your maven project dependency.

Maven dependencies are also Maven projects, so they also have their own “pom.xml” file. This is how dependencies declare their own dependencies, which we call the “transitive dependencies”

- there should be **only one dependency version** in classpath lib, here are approachs to choose the right version taken by maven :
	- nearest definition
	- dependency management
	


<pre>  A
  ├── B
  │   └── C
  │       └── D 2.0
  └── E
      └── D 1.0</pre>
      
in the preceding example {C,D} were transitive dependencies and due to maven nearest definition D version 1.0 will be chosen for project classpath.

## Refrences
- [apache maven docs](https://maven.apache.org/guides/)
- [maven dependency mechanism](https://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html)
