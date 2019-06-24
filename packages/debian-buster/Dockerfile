FROM debian:buster
LABEL maintainer="Seznam.cz a.s."

ENV CONCURRENCY=32

RUN apt-get update && apt-get install --assume-yes \
    apt-transport-https \
    devscripts \
    dpkg-dev \
    equivs \
    make \
    software-properties-common \
    dirmngr \
&& echo "deb [arch=amd64] https://download.docker.com/linux/debian buster stable" >> /etc/apt/sources.list.d/docker.list \
&& curl --fail --silent --show-error --location https://download.docker.com/linux/debian/gpg | apt-key add - >/dev/null 2>&1 \
&& echo "deb http://repo.mysql.com/apt/debian/ buster mysql-5.7" > /etc/apt/sources.list.d/mysql.list \
&& curl --fail --silent --show-error --location https://repo.mysql.com/RPM-GPG-KEY-mysql | apt-key add - >/dev/null 2>&1 \
&& apt-get update

VOLUME /dbuild/sources

ADD docker-run.sh /
ENTRYPOINT ["/bin/sh", "-c", "/docker-run.sh"]
