FROM debian:jessie
MAINTAINER Ofer Affias

ENV REBAR_VERSION beta-1

RUN apt-get update && apt-get install -y wget

RUN echo "deb http://packages.erlang-solutions.com/debian jessie contrib" >> /etc/apt/sources.list
RUN wget http://packages.erlang-solutions.com/ubuntu/erlang_solutions.asc && apt-key add erlang_solutions.asc

RUN apt-get update && apt-get install -y \
  erlang=1:18.0 \
  erlang-base-hipe=1:18.0

ADD https://github.com/rebar/rebar3/archive/${REBAR_VERSION}.tar.gz  /usr/src/rebar3-${REBAR_VERSION}.tar.gz
RUN cd /usr/src \
    && tar zxf rebar3-${REBAR_VERSION}.tar.gz \
    && cd rebar3-${REBAR_VERSION} \
    && escript bootstrap \
    && cp rebar3 /usr/bin/rebar3 \
    && cd / && rm -rf /usr/src/rebar3-${REBAR_VERSION}*

CMD ["erl"]
