use "mvn install" to install this archetype
the archetype catalog file is: ~/.m2/repository/archetype-catalog.xml

create project from this archetype, then run "mvn clean package"
the project will package the project JAR in the target directory, with the dependency files and log4j2 config files.
in target, use follow command to run the JAR:
java -jar <the project JAR file>

change files in src/main/resources/archetype-resources 
and src/main/resources/META-INF to customize the archetype
the project tree is:
.
├── .classpath
├── pom.xml
├── .project
├── .settings
│   ├── org.eclipse.core.resources.prefs
│   ├── org.eclipse.jdt.core.prefs
│   └── org.eclipse.m2e.core.prefs
└── src
    ├── main
    │   ├── java
    │   │   └── App.java
    │   └── resources
    │       └── log4j2.xml
    └── test
        ├── java
        │   └── AppTest.java
        └── resources
            └── log4j2-test.xml
            
pom.xml include the dependencies:
junit
slf4j-api
log4j-slf4j-impl
log4j-core
commons-lang3

pom.xml include the plugins:
maven-shade-plugin

can not auto add .gitignore file to archetype JAR file, why? 
but manual add the .gitignore file to JAR file.
see also:
https://issues.apache.org/jira/browse/ARCHETYPE-505
archetype:create-from-project,the .gitignore file not copy to archetype-resources
fixed: use maven-resources-plugin to copy the .gitignore file to archetype-resources
