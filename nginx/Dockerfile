# DOCKER-VERSION 1.0.0

FROM centos:centos6

## add repository
RUN rpm -ivh http://nginx.org/packages/centos/6/noarch/RPMS/nginx-release-centos-6-0.el6.ngx.noarch.rpm

RUN yum -y update
RUN yum -y install --enablerepo=centosplus openssl-devel

# install Nginx
RUN yum -y install --enablerepo=nginx nginx
ADD etc/nginx/nginx.conf /etc/nginx/nginx.conf
ADD etc/nginx/conf.d/default.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["/usr/sbin/nginx", "-g", "daemon off;"]