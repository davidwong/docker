# Gradle data volume container
##Installation of Gradle into a Docker data volume container.

This allows the Gradle installation to be persisted and shared by other containers.

The container that wants to use this data container to run Gradle must use *--volumes-from* to get access to the Gradle installation directory and also set the require Gradle environmental variables.
e.g.

```
docker run -i -t --volumes-from gradle-2.2.1 -e GRADLE_HOME=/opt/gradle -e PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/opt/gradle/bin yourcontainer
```

Note the parts of the command that relate to the Gradle data volume container:

 * access the Gradle installation with the *--volumes-from* option (in this example the Gradle data container was named *gradle-2.2.1*)
 * set the GRADLE_HOME environmental variable
 * add the Gradle executables directory to the PATH, note that the rest of the PATH environment variable should be replaced by the PATH from your container

Of course your container should have Java installed as it is a requirement to run Gradle.

See the blog post for further explanation:
http://www.davidwong.com.au/blog/....