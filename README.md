## sbt-xjc An SBT 0.10 Plugin to compile XML Schemata to JAXB Java sources with XJC

### Usage:

Depend on the plugin: `./project/plugins/build.sbt`

```
resolvers += "retronym" at "http://retronym.github.com/repo/releases"
libraryDependencies += "com.github.retronym" %% "sbt-xjc" % "0.1"
```

Include the settings from `SbtXjcPlugin.settings`.

Place your XSD files in `./src/main/xsd`, or another configure a custom set of files with `set sources in Xjc := Seq(file("my.xsd"))`

Before compilation, XJC will be invoked to generate sources to `sourceManaged in Xjc`, by default `${target}/src_managed/xjc`.

To use compiler plugins:

```
xjcPlugins     += "net.java.dev.jaxb2-commons" % "jaxb-fluent-api" % "2.1.8",
xjcCommandLine += "-Xfluent-api"
```

As a convenience, the fluent API settings are provided in `SbtXjcPlugin.fluentApiSettings`

### Limitations

Only one invocation per project is supported; this will be added to the `Compile` scope.