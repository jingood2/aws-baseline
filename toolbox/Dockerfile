#FROM theserverlessway/awsinfo:latest
FROM toniblyx/prowler:latest as prowler

#RUN yum install -y build-base gcc libffi-dev openssl-dev openssl musl-dev git curl which python-dev python-devel python3-dev python3-devel

#RUN git clone https://github.com/toniblyx/prowler.git /prowler
#ENV PATH="/prowler:${PATH}"
FROM theserverlessway/awsinfo:latest

WORKDIR /app

COPY requirements.txt requirements.txt
RUN pip3 install -U -r requirements.txt
#RUN pip3 install scoutsuite

RUN mkdir -p /etc/bash_completion.d

RUN awsinfo complete > /root/.awsinfo_completion

RUN activate-global-python-argcomplete
COPY bashrc /root/.bashrc

COPY --from=prowler /prowler /prowler
ENV PATH="/prowler:${PATH}"

ENV PS1='\[\e[0;32m\]\w \[\e[0;32m\]→\[\e[39m\] '

ENTRYPOINT []