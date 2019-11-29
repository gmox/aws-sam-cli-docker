FROM alpine:latest

ENV API_PORT=3000
EXPOSE ${API_PORT}:${API_PORT}

RUN apk -v --update add \
        python3 \
        python3-dev \
        py3-pip \
        wget \
        gcc \
        musl-dev

WORKDIR /aws-sam-cli
RUN wget https://files.pythonhosted.org/packages/2c/4f/cda33dc06da70c6db23aee18ac75185bdc1aac37d7b0aed85d084b61091d/aws-sam-cli-0.34.0.tar.gz && \
    tar -xzf ./aws-sam-cli-0.34.0.tar.gz && \
    cd ./aws-sam-cli-0.34.0 && \
    pip3 install --ignore-installed .

VOLUME /var/run/docker.sock:/var/run/docker.sock
# Allows us to run docker inside of docker
VOLUME ["/var/run/docker.sock"]
ENTRYPOINT ["sam"]
