FROM redis:6
MAINTAINER who "lianyan598@gmail.com"

ENV TZ "Asia/Shanghai"
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN mkdir -p /opt/log \
    && mkdir -p /opt/data \
    && bash -c 'touch /opt/log/redis.log' \
    && bash -c 'chmod 777 -R /opt'


COPY redis-slave.conf /usr/local/etc/redis/redis-slave.conf
CMD [ "redis-server", "/usr/local/etc/redis/redis-slave.conf" ]