FROM alpine:3.7
MAINTAINER Coopengo <support@coopengo.com>

RUN apt-get update && apt-get install -y --no-install-recommends \
        gcc \
        vim \
        libpq-dev \
        libldap2-dev \
        libsasl2-dev \
        redis-tools \
        graphviz \
        libmagic1 \
        git \
	openssh-client \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

ENV PATH="/workspace/bin:${PATH}"

COPY dist /workspace
COPY ep /workspace/bin/

RUN echo $PATH
RUN ls /workspace/bin
RUN ln -s /workspace/trytond/bin/trytond /usr/local/bin \
    && ln -s /workspace/trytond/bin/trytond-admin /usr/local/bin \
    && ln -s /workspace/trytond/bin/trytond-cron /usr/local/bin \
    && ln -s /workspace/ep /usr/local/bin/ep \
    && /workspace/bin/ep link

VOLUME ["/workspace/sao", "/workspace/coog-bench", "/workspace/coog-doc"]
ENTRYPOINT ["ep"]
EXPOSE 8000
