# Install Gradle as a data volume container. 
#
# The app container that uses this container will need to set the Gradle environmental variables.
# - set GRADLE_HOME to the gradle installation directory
# - add the /bin directory under the gradle directory to the PATH

FROM mini/base

MAINTAINER David Wong

# setup location for installation
ENV INSTALL_LOCATION /opt

# install Gradle version required
ENV GRADLE_VERSION 2.2.1

WORKDIR ${INSTALL_LOCATION}
RUN curl -L -O http://services.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip && \
    unzip -qo gradle-${GRADLE_VERSION}-bin.zip && \
    rm -rf gradle-${GRADLE_VERSION}-bin.zip
    
# to make the container more portable, the installation directory name is changed from the default
# gradle-${GRADLE_VERSION} to just gradle, with the version number stored in a text file for reference
# e.g. instead of /opt/gradle-2.2.1, the directory will be /opt/gradle

RUN mv gradle-${GRADLE_VERSION} gradle && \
    echo ${GRADLE_VERSION} > gradle/version
    
VOLUME ${INSTALL_LOCATION}/gradle

# echo to make it easy to grep
CMD /bin/sh -c '/bin/echo Data container for Gradle'