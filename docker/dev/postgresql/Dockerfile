FROM postgres:16

ENV TZ=Asia/Tokyo
ENV LANG=ja_JP.UTF-8
ENV LANGUAGE=ja_JP:ja
ENV LC_ALL=ja_JP.UTF-8


RUN apt-get update && apt-get install -y --no-install-recommends \
    vim \
    locales \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN echo "ja_JP.UTF-8 UTF-8" > /etc/locale.gen && \
    locale-gen ja_JP.UTF-8

RUN mkdir /var/postgres \
    && chown postgres:postgres /var/postgres \
    && rm -rf /etc/postgresql/conf.d

COPY ./postgresql.conf /etc/postgresql/postgresql.conf