FROM centos/s2i-core-centos7

ENV JRE_DOWNLOAD_URL http://download.oracle.com/otn-pub/java/jdk/8u171-b11/512cd62ec5174c3487ac17c61aaa89e8/jre-8u171-linux-x64.rpm
ENV JRE_FOLDER_NAME jre1.8.0_171-amd64

ENV PATH ${PATH}:/usr/java/${JRE_FOLDER_NAME}

RUN rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7  \
    && yum -y install wget which\
    && yum clean all

RUN wget --quiet \
        --no-cookies \
        --no-check-certificate \
        --header "Cookie: oraclelicense=accept-securebackup-cookie" \
        "${JRE_DOWNLOAD_URL}" \
        -O jre.rpm \
    && rpm -Uvh jre.rpm \
    && rm -f jre.rpm

COPY ./s2i/bin $STI_SCRIPTS_PATH

USER 1001
