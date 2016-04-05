# A Dockerfile for Blacklight
FROM ubuntu:14.04

MAINTAINER David Jiao <djiao@iu.edu>

# Install Ruby and nodejs
RUN apt-get update
RUN apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev  python-software-properties libffi-dev liblzma-dev libgmp-dev -y
RUN apt-get install libgdbm-dev libncurses5-dev automake libtool bison libffi-dev -y
RUN gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
RUN curl -L https://get.rvm.io | bash -s stable
RUN /bin/bash -c "source /usr/local/rvm/scripts/rvm"
RUN /bin/bash -l -c "rvm install 2.2.3"
RUN /bin/bash -l -c "rvm use 2.2.3 --default"
RUN curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -
RUN apt-get install -y nodejs

ENV PATH /usr/local/rvm/gems/ruby-2.2.3/bin:/usr/local/rvm/gems/ruby-2.2.3@global/bin:/usr/local/rvm/rubies/ruby-2.2.3/bin:$PATH:/usr/local/rvm/bin

RUN gem install bundler

# # Install Rails
RUN gem install rails

# Download and install blacklight
WORKDIR /opt
RUN rails new search_app -m https://raw.github.com/projectblacklight/blacklight/master/template.demo.rb

WORKDIR /opt/search_app
# RUN rake jetty:start
#RUN rake solr:marc:index_test_datas
CMD bundle exec rails s -p 3000 -b '0.0.0.0'
