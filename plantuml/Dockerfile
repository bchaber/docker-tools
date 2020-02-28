FROM openjdk:14-jdk-alpine3.10
LABEL original-repository="https://github.com/lindt/docker_plantuml"
LABEL original-author="think@hotmail.de"
LABEL maintainer="bartosz.chaber@ee.pw.edu.pl"
ENV PLANTUML_VERSION=1.2019.11
ENV LANG en_US.UTF-8
RUN \
  apk add --no-cache graphviz wget ca-certificates ttf-dejavu fontconfig && \
  wget "http://downloads.sourceforge.net/project/plantuml/${PLANTUML_VERSION}/plantuml.${PLANTUML_VERSION}.jar" -O plantuml.jar && \
  apk del wget ca-certificates
RUN apk add --no-cache font-noto
RUN ["java", "-Djava.awt.headless=true", "-jar", "plantuml.jar", "-version"]
RUN ["dot", "-version"]
ENTRYPOINT ["java", "-Djava.awt.headless=true", "-jar", "plantuml.jar", "-p"]
CMD ["-tsvg"]
