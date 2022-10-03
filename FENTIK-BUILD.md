# Build instructions

Build the the target jar file into `./java/target/rocksdbjni-6.20.3-linux64.jar`

```
make jclean clean rocksdbjavastaticdockerx86_64
```

Now install the jar file into your local Maven repository so that when you build flink,
it will use the local version of rocksdb from the repo instead of getting the dep
from the global repo.

```
mvn org.apache.maven.plugins:maven-install-plugin:3.0.1:install-file  -Dfile=rocksdbjni-6.20.3-linux64.jar -DgroupId=com.ververica -DartifactId=frocksdbjni -Dversion=6.20.3-fentik-1.0 -Dpackaging=jar
```

No go and build `flink`. It will use the local version.
