#invoke npm in jenkinsfile: sh "scl enable rh-nodejs6 'npm run build'"
FROM registry.access.redhat.com/openshift3/jenkins-agent-nodejs-8-rhel7
USER root

RUN yum repolist > /dev/null && \
    INSTALL_PKGS="nss_wrapper redhat-lsb libXScrnSaver xdg-utils wget" && \
    yum install -y --setopt=tsflags=nodocs \
      --enablerepo=rhel-server-rhscl-7-rpms \
      --enablerepo=rhel-7-server-optional-rpms \
      --enablerepo=rhel-7-server-optional-rpms \
      --disablerepo=rhel-7-server-htb-rpms \
      $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    yum clean all -y && \
    rm -rf /var/cache/yum

ADD https://dl.google.com/linux/direct/google-chrome-stable_current_x86_64.rpm google-chrome-stable_current_x86_64.rpm
RUN yum -y localinstall google-chrome-stable_current_x86_64.rpm --disablerepo=rhel-7-server-htb-rpms
ENV CHROME_BIN /bin/google-chrome

USER 1001

RUN git config --global user.email "jenkins@ci-cd.com" && \
    git config --global user.name "jenkins"
