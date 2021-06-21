FROM centos
MAINTAINER zyz<zyzflydream@163.com>
RUN yum -y install wget gcc gcc-c++ make
ADD redis-6.2.4.tar.gz /usr/src/
WORKDIR /usr/src/redis-6.2.4/
RUN make
RUN make MALLOC=jemalloc &&  make PREFIX=/usr/local/redis install
WORKDIR /usr/local/redis/
RUN mkdir -p /usr/local/redis/conf/
RUN cp /usr/src/redis-6.2.4/redis.conf /usr/local/redis/conf/ && cp /usr/src/redis-6.2.4/sentinel.conf /usr/local/redis/conf/
RUN ln -s /usr/local/redis/bin/* /usr/local/bin/
WORKDIR /usr/local/redis/conf/
RUN cp redis.conf{,.bak}
RUN mkdir -p /data/
EXPOSE 6379
CMD redis-server /usr/local/redis/conf/redis.conf

