FROM alpine:3.1

LABEL maintainer="Paolo Oliveira <paolo@fisica.ufc.br>"
LABEL repository="https://github.com/paoloo/sqlmap"

RUN apk add --update python
RUN apk add --update git
RUN git clone https://github.com/sqlmapproject/sqlmap.git

WORKDIR /sqlmap

ENTRYPOINT ["python", "sqlmap.py"]
