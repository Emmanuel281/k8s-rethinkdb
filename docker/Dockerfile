FROM rethinkdb:latest

RUN apt-get update && \
    apt-get install -yq curl && \
    rm -rf /var/cache/apt/* && rm -rf /var/lib/apt/lists/*

ADD https://github.com/jqlang/jq/releases/download/jq-1.7.1/jq-linux-amd64 /usr/bin/jq
RUN chmod +x /usr/bin/jq

COPY ./run.sh ./probe ./ready-probe.sh /
RUN sed -i 's/\r$//' /run.sh && \
    chmod u+x /run.sh /probe /ready-probe.sh

ENTRYPOINT ["/bin/bash", "/run.sh"]

