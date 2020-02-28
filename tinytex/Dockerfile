FROM alpine:3.9
LABEL original-repository="https://github.com/wadedos/alpine-tinytex"
LABEL original-author="Wade Wildbore (wadedos)"
LABEL maintainer="bartosz.chaber@ee.pw.edu.pl"
# tinytex dependencies
RUN apk --no-cache add \
  perl  \
  wget \
  xz \
  tar \
  fontconfig \
  freetype \
  lua \
  gcc

# add user
RUN addgroup -S tex && adduser -S tex -G tex --home /home

# install as tex
USER tex

# setup workdir
WORKDIR /home

# setup path
ENV PATH=/home/.TinyTeX/bin/x86_64-linuxmusl/:$PATH

# download and install tinytex
RUN wget -qO- "https://yihui.name/gh/tinytex/tools/install-unx.sh" | sh

# add tlmgr to path
RUN /home/.TinyTeX/bin/*/tlmgr path add

# verify latex version
RUN latex --version

# verify tlmgr version
RUN tlmgr --version

# install texlive packages
RUN tlmgr install \
    preview \
    standalone \
    dvisvgm

# verify 
RUN dvisvgm --version

USER tex
RUN mkdir -p /home/tex
WORKDIR /home/tex
ENTRYPOINT ["pdflatex"]
