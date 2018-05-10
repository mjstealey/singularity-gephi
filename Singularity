Bootstrap: yum
OSVersion: 7
MirrorURL: http://mirror.centos.org/centos-%{OSVERSION}/%{OSVERSION}/os/$basearch/
Include: yum

%help
  Gephi - The Open Graph Viz Platform
  Version 0.9.2

  Usage:
  $ singularity run gephi.0.9.2.simg [args]
  $ singularity run --app gephi gephi.0.9.2.simg [args]

%setup

%files

%labels
  Maintainer Michael J. Stealey
  Maintainer_Email stealey@renci.org
  Gephi_Version 0.9.2
  Java_Version 1.8.0_171

%environment
  JAVA_VERSION=1.8.0_171
  GEPHI_VERSION=0.9.2

%post
  export JAVA_VERSION=1.8.0_171
  export GEPHI_VERSION=0.9.2
  yum -y install \
    tar \
    which \
    gzip \
    libXext \
    libXrender \
    libXtst

  # install java 1.8.0_xxx
  RPM_URL=$(curl -s https://lv.binarybabel.org/catalog-api/java/jdk8.txt?p=downloads.rpm)
  curl -LOH 'Cookie: oraclelicense=accept-securebackup-cookie' "${RPM_URL}"
  yum -y localinstall jdk-*.rpm
  rm -f jdk-*.rpm
  export JAVA_HOME=/usr/java/jdk${JAVA_VERSION}-amd64
  export JRE_HOME=/usr/java/jdk${JAVA_VERSION}-amd64/jre/bin
  export PATH=/usr/java/jdk${JAVA_VERSION}-amd64/bin:$PATH

  # install gephi
  cd /usr/local
  curl -L https://github.com/gephi/gephi/releases/download/v${GEPHI_VERSION}/gephi-${GEPHI_VERSION}-linux.tar.gz -o gephi-${GEPHI_VERSION}-linux.tar.gz
  tar xzvf gephi-${GEPHI_VERSION}-linux.tar.gz
  rm -f gephi-${GEPHI_VERSION}-linux.tar.gz
  export PATH=/usr/local/gephi-${GEPHI_VERSION}/bin:$PATH
  cd /

  # create init.sh
  cat > /usr/local/init.sh <<EOF
#!/usr/bin/env bash
export JAVA_HOME=/usr/java/jdk${JAVA_VERSION}-amd64
export JRE_HOME=/usr/java/jdk${JAVA_VERSION}-amd64/jre/bin
export PATH=/usr/java/jdk${JAVA_VERSION}-amd64/bin:\$PATH
export PATH=/usr/local/gephi-${GEPHI_VERSION}/bin:\$PATH
EOF
  chmod a+x /usr/local/init.sh

%apprun gephi
  source /usr/local/init.sh
  exec gephi "${@}"

%runscript
  source /usr/local/init.sh
  exec "${@}"

%test
  source /usr/local/init.sh
  env
