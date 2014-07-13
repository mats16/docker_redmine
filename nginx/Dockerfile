# DOCKER-VERSION 1.0.0

FROM centos:centos6

## add repository
RUN rpm -ivh http://ftp.riken.jp/Linux/fedora/epel/6/x86_64/epel-release-6-8.noarch.rpm \
             http://rpms.famillecollet.com/enterprise/remi-release-6.rpm

RUN yum -y update
RUN yum -y install --enablerepo=centosplus openssl-devel
RUN yum -y install --enablerepo=remi nginx

ADD etc/nginx/nginx.conf /etc/nginx/nginx.conf
ADD etc/nginx/conf.d/default.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD nginx -g 'daemon off;'