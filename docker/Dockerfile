FROM arm32v7/openjdk:jre

ENV FILEBOT_VERSION 4.7.9
ENV FILEBOT_PACKAGE filebot_${FILEBOT_VERSION}-portable.tar.xz

WORKDIR /usr/share/filebot


RUN apt-get update && apt-get install -y \
    mediainfo \
    libchromaprint-tools \
    file \
    curl \
    inotify-tools \
 && rm -rf /var/lib/apt/lists/*


RUN curl -L -O https://downloads.sourceforge.net/project/filebot/filebot/FileBot_$FILEBOT_VERSION/$FILEBOT_PACKAGE
RUN tar zxf $FILEBOT_PACKAGE 
RUN rm $FILEBOT_PACKAGE

ENV DOCKER_DATA /data
ENV DOCKER_VOLUME /volume1


ENV HOME $DOCKER_DATA
ENV JAVA_OPTS "-DuseGVFS=false -Djava.net.useSystemProxies=false -Dapplication.deployment=docker -Dapplication.dir=$DOCKER_DATA -Duser.home=$DOCKER_DATA -Djava.io.tmpdir=$DOCKER_DATA/tmp -Djava.util.prefs.PreferencesFactory=net.filebot.util.prefs.FilePreferencesFactory -Dnet.filebot.util.prefs.file=$DOCKER_DATA/prefs.properties"


WORKDIR $DOCKER_DATA

VOLUME ["$DOCKER_DATA", "$DOCKER_VOLUME"]

ENTRYPOINT ["filebot"]
