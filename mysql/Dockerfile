# DOCKER-VERSION 1.0.0

FROM centos:centos6

## add repository
RUN rpm -ivh http://ftp.riken.jp/Linux/fedora/epel/6/x86_64/epel-release-6-8.noarch.rpm \
             http://rpms.famillecollet.com/enterprise/remi-release-6.rpm

RUN yum -y update
RUN yum -y install --enablerepo=centosplus openssl-devel
RUN yum -y install --enablerepo=remi mysql-server mysql-devel mysql

ADD etc/my.cnf /etc/my.cnf

RUN mysql_install_db

# alternative to　"mysql_secure_installation"
RUN /etc/init.d/mysqld start && \
    mysqladmin -u root password "root" && \
    mysql -u root -proot -e "DELETE FROM mysql.user WHERE User='';" && \
    mysql -u root -proot -e "DELETE FROM mysql.user WHERE User='root' AND Host NOT IN ('localhost', '127.0.0.1');" && \
    mysql -u root -proot -e "DROP DATABASE test;" && \
    mysql -u root -proot -e "DELETE FROM mysql.db WHERE Db='test' OR Db='test\\_%';" && \
    mysql -u root -proot -e "CREATE DATABASE redmine DEFAULT CHARACTER SET utf8;" && \
    mysql -u root -proot -e "GRANT ALL PRIVILEGES ON redmine.* TO redmine@'%' IDENTIFIED BY 'redmine' WITH GRANT OPTION;" && \
    mysql -u root -proot -e "FLUSH PRIVILEGES;" && \
    /etc/init.d/mysqld stop

EXPOSE 3306
CMD ["/usr/bin/mysqld_safe"]