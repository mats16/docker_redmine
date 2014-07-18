# DOCKER-VERSION 1.0.0

FROM centos:centos6

ENV REDMINE_VERSION 2.5-stable
ENV REDMINE_HOME /var/redmine
ENV RAILS_ENV production
ENV UNICORN_PORT 8080

## add repository
RUN rpm -ivh http://ftp.riken.jp/Linux/fedora/epel/6/x86_64/epel-release-6-8.noarch.rpm \
             http://rpms.famillecollet.com/enterprise/remi-release-6.rpm

RUN yum -y update
RUN yum -y groupinstall "Development Tools"
RUN yum -y install --enablerepo=centosplus openssl-devel
RUN yum -y install --enablerepo=remi mysql-devel mysql
RUN yum -y install git \
                   readline-devel \
                   zlib-devel curl-devel \
                   libyaml-devel \
                   ImageMagick \
                   ImageMagick-devel \
                   ipa-pgothic-fonts

# install Ruby
ADD http://ftp.ruby-lang.org/pub/ruby/ruby-2.1.0.tar.gz /usr/local/src/
WORKDIR /usr/local/src
RUN tar xfz ruby-2.1.0.tar.gz
WORKDIR /usr/local/src/ruby-2.1.0
RUN ./configure --disable-install-doc && make && make install
RUN gem install bundler --no-rdoc --no-ri

# install Redmine
RUN git clone -b ${REDMINE_VERSION} https://github.com/redmine/redmine.git ${REDMINE_HOME}

ADD redmine/database.yml ${REDMINE_HOME}/config/database.yml
ADD redmine/configuration.yml ${REDMINE_HOME}/config/configuration.yml
ADD redmine/unicorn.rb ${REDMINE_HOME}/config/unicorn.rb
ADD redmine/Gemfile.local ${REDMINE_HOME}/Gemfile.local
RUN mkdir ${REDMINE_HOME}/public/plugin_assets

EXPOSE 80
WORKDIR /var/redmine
CMD bundle install --without development test && \
    bundle exec rake generate_secret_token && \
    bundle exec rake db:migrate RAILS_ENV=${RAILS_ENV} && \
    bundle exec unicorn -c config/unicorn.rb -E ${RAILS_ENV} -p 8080