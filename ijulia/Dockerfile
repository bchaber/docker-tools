FROM "jupyter/minimal-notebook"
LABEL original-repository="https://github.com/andferrari/julia_notebook"
LABEL original-author="André Ferrari (andferrari)"
LABEL maintainer="bartosz.chaber@ee.pw.edu.pl"
USER root

ENV JULIA_VERSION=1.3.1

RUN mkdir /opt/julia-${JULIA_VERSION} && \
    cd /tmp && \
    wget -q https://julialang-s3.julialang.org/bin/linux/x64/`echo ${JULIA_VERSION} | cut -d. -f 1,2`/julia-${JULIA_VERSION}-linux-x86_64.tar.gz && \
    tar xzf julia-${JULIA_VERSION}-linux-x86_64.tar.gz -C /opt/julia-${JULIA_VERSION} --strip-components=1 && \
    rm /tmp/julia-${JULIA_VERSION}-linux-x86_64.tar.gz

RUN ln -fs /opt/julia-*/bin/julia /usr/local/bin/julia

USER $NB_UID

# Add packages and precompile
 
RUN julia -e 'import Pkg; Pkg.update()' && \
    julia -e 'import Pkg; Pkg.add("GR"); import GR' && \    
    julia -e 'import Pkg; Pkg.add("CSV"); import CSV' && \    
    julia -e 'import Pkg; Pkg.add("Plots"); import Plots' && \    
    julia -e 'import Pkg; Pkg.add("StatsPlots"); import StatsPlots' && \    
    julia -e 'import Pkg; Pkg.add("Distributions"); import Distributions' && \
    julia -e 'import Pkg; Pkg.add("Interpolations"); import Interpolations' && \
    julia -e 'import Pkg; Pkg.add("BenchmarkTools"); import BenchmarkTools' && \
    julia -e 'import Pkg; Pkg.add("DataStructures"); import DataStructures' && \
    julia -e 'import Pkg; Pkg.add("PyCall"); import PyCall' && \
    julia -e 'import Pkg; Pkg.add("IJulia"); import IJulia' && \
    fix-permissions /home/$NB_USER

