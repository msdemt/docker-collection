FROM centos:7.9.2009

RUN set -ex \
    # support chinese
    && yum install -y kde-l10n-Chinese glibc-common \
    && localedef -c -f UTF-8 -i zh_CN zh_CN.utf8 \
    && echo 'LANG="zh_CN.UTF-8"' > /etc/locale.conf \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    # add jdk
    && curl -O https://msdemt.github.io/resources/jdk8u202.tar.gz0[0-7] \
    && cat jdk8u202.tar.gz* | tar -zxf - \
    && tar -zxf jdk-8u202-linux-x64.tar.gz -C /usr/local \
    && ln -s /usr/local/jdk1.8.0_202 /usr/local/jdk \
    && echo -e '#!/bin/bash\nexport JAVA_HOME=/usr/local/jdk\nexport CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar\ncase ":$PATH:" in\n    *":$JAVA_HOME/bin:"*) :;; \n    *) PATH="$JAVA_HOME/bin:$PATH";;\nesac' > /etc/profile.d/jdk.sh \
    && source /etc/profile \
    && rm -rf jdk8u202.tar.gz* jdk-8u202-linux-x64.tar.gz \
    && rm -rf   /var/log/* \
                /var/cache/* \
                /tmp/* \
                ${JAVA_HOME}/*src.zip \
                ${JAVA_HOME}/man \
                ${JAVA_HOME}/*.txt \
                ${JAVA_HOME}/*.html \
                ${JAVA_HOME}/COPYRIGHT \
                ${JAVA_HOME}/LICENSE \
                ${JAVA_HOME}/release \
                ${JAVA_HOME}/bin/jmc* \
                ${JAVA_HOME}/bin/jvisualvm \
                ${JAVA_HOME}/bin/*javafx* \
                ${JAVA_HOME}/bin/appletviewer \
                ${JAVA_HOME}/bin/javapackager \
                ${JAVA_HOME}/bin/jconsole \
                ${JAVA_HOME}/bin/ControlPanel \
                ${JAVA_HOME}/bin/jcontrol \
                ${JAVA_HOME}/lib/missioncontrol \
                ${JAVA_HOME}/lib/visualvm \
                ${JAVA_HOME}/lib/*javafx* \
                ${JAVA_HOME}/lib/jconsole.jar \
                ${JAVA_HOME}/lib/packager.jar \
                ${JAVA_HOME}/jre/*.txt \
                ${JAVA_HOME}/jre/*.html \
                ${JAVA_HOME}/jre/COPYRIGHT \
                ${JAVA_HOME}/jre/LICENSE \
                ${JAVA_HOME}/jre/README \
                ${JAVA_HOME}/jre/plugin \
                ${JAVA_HOME}/jre/bin/ControlPanel \
                ${JAVA_HOME}/jre/bin/jcontrol \
                ${JAVA_HOME}/jre/lib/deploy* \
                ${JAVA_HOME}/jre/lib/desktop \
                ${JAVA_HOME}/jre/lib/*javafx* \
                ${JAVA_HOME}/jre/lib/*jfx* \
                ${JAVA_HOME}/jre/lib/oblique-fonts \
                ${JAVA_HOME}/jre/lib/plugin.jar \
                ${JAVA_HOME}/jre/lib/amd64/libavplugin*.so \
                ${JAVA_HOME}/jre/lib/amd64/libde*.so \
                ${JAVA_HOME}/jre/lib/amd64/libfxplugins.so \
                ${JAVA_HOME}/jre/lib/amd64/libgl*.so \
                ${JAVA_HOME}/jre/lib/amd64/libgstreamer-lite.so \
                ${JAVA_HOME}/jre/lib/amd64/libjavafx*.so \
                ${JAVA_HOME}/jre/lib/amd64/libjfx*.so \
                ${JAVA_HOME}/jre/lib/amd64/libnpjp2.so \
                ${JAVA_HOME}/jre/lib/amd64/libprism_*.so \
                ${JAVA_HOME}/jre/lib/amd64/libfxplugins.so \
                ${JAVA_HOME}/jre/lib/amd64/server/libjsig.so \
                ${JAVA_HOME}/jre/lib/deploy \
                ${JAVA_HOME}/jre/lib/images/icons \
                ${JAVA_HOME}/jre/lib/locale \
                ${JAVA_HOME}/jre/lib/ext/jfxrt.jar \
                ${JAVA_HOME}/jre/lib/ext/jaccess.jar \
    && ln -s ${JAVA_HOME}/jre/lib/amd64/libjsig.so ${JAVA_HOME}/jre/lib/amd64/server/libjsig.so

ENV LANG zh_CN.UTF-8
ENV LC_ALL zh_CN.UTF-8

CMD ["/bin/bash"]
