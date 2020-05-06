FROM nginx

RUN DEBIAN_FRONTEND=noninteractive apt-get update -qq && \
    apt-get -y install wget runit unzip && \
    rm -rf /var/lib/apt/lists/*

# vim - debug purposes
RUN apt-get update && apt-get -y install vim
RUN apt-get install -y procps

RUN wget https://releases.hashicorp.com/consul/1.7.2/consul_1.7.2_linux_386.zip
# install consul-template
RUN unzip -d /usr/local/bin consul_1.7.2_linux_386.zip && rm consul_1.7.2_linux_386.zip

ADD nginx.service /etc/service/nginx/run
ADD consul-template.service /etc/service/consul-template/run

RUN mkdir /etc/consul-template && chmod +x /etc/service/nginx/run && chmod +x /etc/service/consul-template/run

CMD ["/usr/bin/runsvdir", "/etc/service"]