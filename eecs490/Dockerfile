FROM jameslp/autograder-sandbox:3.1.2

RUN apt-get update
RUN apt-get install -y software-properties-common python3-software-properties

RUN add-apt-repository ppa:plt/racket
RUN add-apt-repository ppa:webupd8team/java
RUN add-apt-repository ppa:swi-prolog/stable
RUN add-apt-repository ppa:deadsnakes/ppa
RUN add-apt-repository ppa:ubuntu-toolchain-r/test

RUN apt-get update

RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
    apt-get install -y oracle-java8-installer
RUN apt-get install -y racket swi-prolog python3.6

ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

RUN apt-get install -y python3.6-dev
RUN wget https://bootstrap.pypa.io/get-pip.py -O /tmp/get-pip.py
RUN python3.6 /tmp/get-pip.py
RUN python3.6 -m pip install numpy

ENV OPENBLAS_NUM_THREADS 1
ENV GOTO_NUM_THREADS 1
ENV OMP_NUM_THREADS 1

ENV JAVA_TOOL_OPTIONS -Xms512m -Xmx512m -XX:+UseSerialGC -XX:MaxMetaspaceSize=256m -XX:CompressedClassSpaceSize=128m

RUN apt-get install -y g++-7

COPY requirements.txt .
RUN python3.6 -m pip install -r requirements.txt
RUN rm requirements.txt
