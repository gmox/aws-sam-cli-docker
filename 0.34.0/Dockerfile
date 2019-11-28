FROM alpine:latest

RUN apk -v --update add \
        python3 \
        python3-dev \
        py3-pip \
        wget \
        gcc \
        musl-dev

WORKDIR /aws-sam-cli
RUN wget --quiet https://files.pythonhosted.org/packages/2c/4f/cda33dc06da70c6db23aee18ac75185bdc1aac37d7b0aed85d084b61091d/aws-sam-cli-0.34.0.tar.gz && \
    tar -xzf ./aws-sam-cli-0.34.0.tar.gz

WORKDIR ./aws-sam-cli-0.34.0
RUN pip3 install --ignore-installed .

WORKDIR /app
ENTRYPOINT ["sam"]
