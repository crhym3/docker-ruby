FROM google/debian:wheezy

RUN apt-get update && apt-get install -y wget openssl ca-certificates libreadline6 libyaml-0-2 libxml2 libxslt1.1
RUN apt-get install -y build-essential libreadline-dev libyaml-dev libncurses5-dev libssl-dev libxml2-dev libxslt1-dev
ADD http://cache.ruby-lang.org/pub/ruby/2.0/ruby-2.0.0-p481.tar.gz /ruby.tar.gz
RUN mkdir /ruby-src && tar xzf ruby.tar.gz --strip-components=1 -C /ruby-src

WORKDIR /ruby-src
RUN ./configure --prefix=/usr --sysconfdir=/etc --disable-install-doc
RUN make && make install

WORKDIR /
RUN rm -rf /ruby.tar.gz /ruby-src
RUN apt-get remove -y libreadline-dev libyaml-dev libncurses5-dev libssl-dev libxml2-dev libxslt1-dev build-essential && apt-get autoremove -y

ADD ./gemrc /etc/gemrc
RUN gem install bundler

