FROM ubuntu:latest

ENV KASPA_VERSION=v0.13.3

WORKDIR /kaspa

RUN apt-get update -y
RUN apt-get install -y wget curl unzip vim

RUN wget https://github.com/kaspanet/rusty-kaspa/releases/download/${KASPA_VERSION}/rusty-kaspa-${KASPA_VERSION}-linux-gnu-amd64.zip
RUN unzip rusty-kaspa-${KASPA_VERSION}-linux-gnu-amd64.zip
RUN ls -al ./bin
RUN cp ./bin/* /usr/bin/

COPY scripts/*.bash /scripts/

RUN useradd -r kaspa
RUN mkdir -p /home/kaspa/.rusty-kaspa
RUN chown kaspa:kaspa /home/kaspa/.rusty-kaspa

USER kaspa

CMD ["/scripts/start.bash"]
