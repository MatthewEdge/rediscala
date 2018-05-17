# rediscala [![Build Status](https://travis-ci.org/Ma27/rediscala.svg)](https://travis-ci.org/Ma27/rediscala) [![Coverage Status](https://img.shields.io/coveralls/Ma27/rediscala.svg)](https://coveralls.io/r/Ma27/rediscala?branch=master) [![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.github.Ma27/rediscala_2.11/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.github.Ma27/rediscala_2.11)

`rediscala` is a [Redis](http://redis.io/) client for [Scala](https://www.scala-lang.org/) (2.11+)
and ([Akka](https://akka.io/) 2.5+) with non-blocking and asynchronous I/O operations:

 * **Reactive** : Redis requests/replies are wrapped in Futures.

 * **Typesafe** : Redis types are mapped to Scala types.

 * **Fast**: Rediscala uses redis pipelining. Blocking redis commands are moved into their own connection.
A worker actor handles I/O operations (I/O bounds), another handles decoding of Redis replies (CPU bounds).

### State of the project

This is an unofficial fork from [etaty/rediscala](https://github.com/etaty/rediscala) started as a
result of the discussion in [etaty/rediscala#191](https://github.com/etaty/rediscala/pull/191).
It's currently maintained by [@herzrasen](https://github.com/herzrasen),
[@kardapoltsev](https://github.com/kardapoltsev) and [@Ma27](https://github.com/Ma27/).

**Please** keep in mind that we mainly intend to maintain this project for the future, but no
active feature development. In case you'd like to help out, feel free to
[open an issue](https://github.com/Ma27/rediscala/issues/new).

### Installation

The build artifacts live in the [Maven Central](http://search.maven.org/#search%7Cga%7C1%7Ccom.github.Ma27.rediscala) repository
and can be installed with [SBT](https://www.scala-sbt.org/):

``` scala
# build.sbt
libraryDependencies += "com.github.Ma27" %% "rediscala" % "1.8.3"
```

### Contributing

The easiest way to start hacking on this project is using [Nix](https://nixos.org/nix/) to build a simple
development environment:

```
$ nix-shell --run "sbt test"
```

It's develop on other distros such as [Ubuntu](https://www.ubuntu.com/):

```
$ apt install sbt redis-server ruby redis-tools
$ export REDIS_TRIB_DIR=/usr/share/doc/redis-tools/examples
$ sbt test
```

### Benchmarks

The codebase has been benchmarked using [ScalaMeter](http://scalameter.github.io/) according to which
this library is able to serve about [250,000 requests per second](http://bit.ly/rediscalabench-1-1).

The benchmarks can be run locally using the `bench` build in SBT:

```
$ nix-shell --run "sbt bench/test"
```

The results can be found in `rediscala/tmp/report/index.html`.
