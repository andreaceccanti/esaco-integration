FROM centos:7

RUN yum -y install epel-release && \
      yum -y update && \
      yum -y install httpd curl && \
      yum -y install https://github.com/zmartzone/mod_auth_openidc/releases/download/v2.3.0/cjose-0.5.1-1.el7.centos.x86_64.rpm && \
      yum -y install https://github.com/zmartzone/mod_auth_openidc/releases/download/v2.3.3/mod_auth_openidc-2.3.3-1.el7.centos.x86_64.rpm 

COPY ./apache-conf.conf /etc/httpd/conf.d
COPY ./igi-test-ca.pem /etc/pki/ca-trust/source/anchors
COPY public-html /var/www/html

RUN update-ca-trust

CMD ["/usr/sbin/httpd", "-DFOREGROUND", "-e", "debug"]
