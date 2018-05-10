# Singularity Gephi: The Open Graph Viz Platform

[![https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg](https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg)](https://singularity-hub.org/collections/798)
[![GitHub License](https://img.shields.io/badge/license-MIT-green.svg)](https://opensource.org/licenses/MIT)


Singularity image for [Gephi 0.9.2](https://gephi.org).

## Build

You can build a local Singularity image named `gephi.0.9.2.simg` with:

```
$ sudo singularity build gephi.0.9.2.simg Singularity
```

## Deploy

Instead of building it yourself you can download the pre-built image from
[Singularity Hub](https://www.singularity-hub.org) with:

```bash
singularity pull --name gephi.0.9.2.simg shub://mjstealey/singularity-gephi
```

## Usage

Help

```console
$ singularity help gephi.0.9.2.simg


  Gephi - The Open Graph Viz Platform
  Version 0.9.2

  Usage:
  $ singularity run gephi.0.9.2.simg [args]
  $ singularity run --app gephi gephi.0.9.2.simg [args]

```

## Run

No particular command is launched using the default run command, rather it is left to the user to specify:

```bash
singularity run gephi.0.9.2.simg [args]
```

Where `[args]` is generally one of {`gephi`, `gephi [args]`}

Example

```console
$ singularity run gephi.0.9.2.simg gephi --nosplash --help
Usage: /usr/local/gephi-0.9.2/bin/../platform/lib/nbexec {options} arguments

General options:
  --help                show this help
  --jdkhome <path>      path to Java(TM) 2 SDK, Standard Edition
  -J<jvm_option>        pass <jvm_option> to JVM

  --cp:p <classpath>    prepend <classpath> to classpath
  --cp:a <classpath>    append <classpath> to classpath
Module reload options:
  --reload /path/to/module.jar  install or reinstall a module JAR file

Additional module options:
  -o, --open <arg1>...<argN>
  --modules
  --refresh                  Refresh all catalogs
  --list                     Prints the list of all modules, their versions and enablement status
  --install <arg1>...<argN>  Installs provided JAR files as modules
  --disable <arg1>...<argN>  Disable modules for specified codebase names
  --enable <arg1>...<argN>   Enable modules for specified codebase names
  --update <arg1>...<argN>   Updates all or specified modules
  --update-all               Updates all modules
  --extra-uc <arg>           Add a extra Update Center (URL)

Core options:
  --laf <LaF classname> use given LookAndFeel class instead of the default
  --fontsize <size>     set the base font size of the user interface, in points
  --locale <language[:country[:variant]]> use specified locale
  --userdir <path>      use specified directory to store user settings
  --cachedir <path>     use specified directory to store user cache, must be different from userdir
  --nosplash            do not show the splash screen

```

### gephi

The `gephi` command is launched as an explicit app:

```bash
singularity run --app gephi gephi.0.9.2.simg [args]
```

Example:

```console
$ singularity run --app gephi gephi.0.9.2.simg --nosplash
```

**Gephi Desktop UI**: (using X11)

<img width="80%" alt="Gephi Desktop UI" src="https://user-images.githubusercontent.com/5332509/39847302-d693f426-53ce-11e8-95cd-9a5e387456fc.png">


## Contributing

Bug reports and pull requests are welcome on GitHub at [https://github.com/mjstealey/singularity-gephi](https://github.com/mjstealey/singularity-gephi).

## License

The code is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
