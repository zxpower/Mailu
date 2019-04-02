ARG EDGE_DISTRO=alpine:edge
FROM $EDGE_DISTRO

RUN echo "@testing http://nl.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories \
  && apk add --no-cache py3-dulwich@testing curl bash
RUN pip3 install radicale

COPY radicale.conf /radicale.conf

EXPOSE 5232/tcp
VOLUME ["/data"]

CMD radicale -f -S -C /radicale.conf

HEALTHCHECK CMD curl -f -L http://localhost:5232/ || exit 1
