FROM redis

EXPOSE 6379

RUN mkdir -p /usr/local/redis/conf

Copy ./conf/redis.conf /usr/local/redis/conf/redis.conf

RUN usermod -u 1000 redis

CMD ["redis-server", "/usr/local/redis/conf/redis.conf"]
