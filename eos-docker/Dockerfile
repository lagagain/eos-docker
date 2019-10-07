FROM ubuntu:18.04
MAINTAINER lagagain

WORKDIR "/root"
RUN mkdir Download

RUN apt update
RUN apt install -y wget

WORKDIR "/root/Download"
RUN wget https://github.com/EOSIO/eos/releases/download/v1.7.0/eosio_1.7.0-1-ubuntu-18.04_amd64.deb
RUN apt install -y ./eosio_1.7.0-1-ubuntu-18.04_amd64.deb

RUN wget https://github.com/EOSIO/eosio.cdt/releases/download/v1.6.1/eosio.cdt_1.6.1-1_amd64.deb
RUN apt install -y ./eosio.cdt_1.6.1-1_amd64.deb

EXPOSE 8888
EXPOSE 8889

WORKDIR "/root"

CMD ["nodeos", "-e", "-p", "eosio", "--plugin", "eosio::producer_plugin", "--plugin", "eosio::chain_api_plugin", "--plugin", "eosio::http_plugin", "--plugin", "eosio::history_plugin", "--plugin", "eosio::history_api_plugin", "--access-control-allow-origin='*'", "--contracts-console", "--http-validate-host=false", "--http-server-address=0.0.0.0:8888", "--verbose-http-errors", "--filter-on", '"*"', "|" , "tee", "nodeos.log"]
