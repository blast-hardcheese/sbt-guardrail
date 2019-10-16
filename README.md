sbt-guardrail
=============

An SBT 1.x+ plugin for adding clients and servers generated by [guardrail](https://github.com/twilio/guardrail) to your service.

Installation
------------

### `project/plugins.sbt`
```
addSbtPlugin("com.twilio" % "sbt-guardrail" % "<Please use the latest available release!>")
```

### `build.sbt`
```
/* Available arguments:
    specPath: java.io.File
    pkg: String
    dto: String
    framework: String
    modules: List[String]
    tracing: Boolean
    imports: List[String]
*/
guardrailTasks in Compile := List(
  ScalaClient(file("petstore.yaml")),
  ScalaClient(file("github.yaml"), pkg="com.example.clients.github"),
  ScalaServer(file("myserver.yaml"), pkg="com.example.server", tracing=true),
  ScalaModels(file("myserver.yaml"), pkg="com.example.models"),
  JavaClient(file("github.yaml"), pkg="com.example.clients.github")
  ...
)
```
