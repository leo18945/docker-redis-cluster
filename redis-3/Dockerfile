FROM redis:4.0.2-alpine

MAINTAINER Tommy Elmesewdy <r1tommy@gmail.com>

COPY localtime /etc/localtime
RUN echo "Asia/Shanghai" > /etc/timezone

EXPOSE 7002
ADD redis.conf /etc/redis/redis.conf
#RUN chown redis:redis /etc/redis/redis.conf
#ADD sentinel-entrypoint.sh /usr/local/bin/
#RUN chmod +x /usr/local/bin/redis-entrypoint.sh
#ENTRYPOINT ["redis-entrypoint.sh"]
