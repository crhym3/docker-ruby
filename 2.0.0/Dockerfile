FROM google/debian:wheezy

RUN apt-get update && apt-get install -y wget build-essential openssl ca-certificates libreadline-dev libyaml-dev libncurses-dev libssl-dev libxml2-dev libxslt-dev
RUN wget --no-verbose http://cache.ruby-lang.org/pub/ruby/2.0/ruby-2.0.0-p481.tar.gz -O ruby.tar.gz
RUN mkdir /ruby-src && tar xzf ruby.tar.gz --strip-components=1 -C /ruby-src

WORKDIR /ruby-src
RUN ./configure --prefix=/usr --sysconfdir=/etc --disable-install-doc
RUN make && make install

WORKDIR /
RUN rm -rf /ruby.tar.gz /ruby-src

ADD ./gemrc /etc/gemrc
RUN gem install bundler

