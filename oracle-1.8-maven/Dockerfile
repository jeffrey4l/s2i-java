FROM centos/s2i-core-centos7

ENV MAVEN_VERSION 3.5.3
ENV JDK_FOLDERNAME jdk1.8.0_171-amd64

ENV PATH ${PATH}:/opt/apache-maven-${MAVEN_VERSION}/bin:/usr/java/${JDK_FOLDERNAME}

RUN rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7  \
    && yum -y install wget which \
    && yum clean all

RUN wget https://mirrors.tuna.tsinghua.edu.cn/apache/maven/maven-3/${MAVEN_VERSION}/binaries/apache-maven-${MAVEN_VERSION}-bin.tar.gz \
        -O apache-maven.tar.gz \
    && tar xvf apache-maven.tar.gz -C /opt \
    && rm -f apache-maven.tar.gz

RUN wget --no-cookies \
        --no-check-certificate \
        --header "Cookie: oraclelicense=accept-securebackup-cookie" \
        "http://download.oracle.com/otn-pub/java/jdk/8u171-b11/512cd62ec5174c3487ac17c61aaa89e8/jdk-8u171-linux-x64.rpm" \
        -O jdk-8-linux-x64.rpm \
    && rpm -Uvh jdk-8-linux-x64.rpm \
    && rm -f jdk-8-linux-x64.rpm

ENV M2_HOME /opt/apache-maven-${MAVEN_VERSION}

COPY ./s2i/bin $STI_SCRIPTS_PATH

USER 1001
