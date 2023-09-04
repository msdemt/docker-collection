FROM centos:7.9.2009 AS build
RUN set -ex \
    && curl -O https://msdemt.github.io/resources/jdk8u202.tar.gz0[0-7] \
    && cat jdk8u202.tar.gz* | tar -zxf - \
   && tar -zxf jdk-8u202-linux-x64.tar.gz -C /usr/local \
    && ln -s /usr/local/jdk1.8.0_202 /usr/local/jdk \
    && echo -e '#!/bin/bash\nexport JAVA_HOME=/usr/local/jdk\nexport CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar\ncase ":$PATH:" in\n    *":$JAVA_HOME/bin:"*) :;; # already there\n    *) PATH="$JAVA_HOME/bin:$PATH";; # or PATH="$PATH:$new_entry"\nesac' > /etc/profile.d/jdk.sh \
    && rm -rf jdk8u202.tar.gz* jdk-8u202-linux-x64.tar.gz

FROM centos:7.9.2009
ENV LANG zh_CN.UTF-8
ENV LC_ALL zh_CN.UTF-8
RUN set -ex \
    && localedef -c -f UTF-8 -i zh_CN zh_CN.utf8 \
    && echo 'LANG="zh_CN.UTF-8"' > /etc/locale.conf \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
COPY --from=build /usr/local/jdk1.8.0_202 /usr/local
RUN set -ex \
    && ln -s /usr/local/jdk1.8.0_202 /usr/local/jdk \
    && echo -e '#!/bin/bash\nexport JAVA_HOME=/usr/local/jdk\nexport CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar\ncase ":$PATH:" in\n    *":$JAVA_HOME/bin:"*) :;; # already there\n    *) PATH="$JAVA_HOME/bin:$PATH";; # or PATH="$PATH:$new_entry"\nesac' > /etc/profile.d/jdk.sh
CMD ["/bin/bash"]
