FROM ubuntu:18.04

RUN apt-get update
RUN apt-get -y upgrade
RUN apt-get install -y apt-utils vim
RUN apt-get install -y sudo

RUN sudo apt-get install -y fortune
RUN sudo apt-get install -y cowsay
RUN ln -s /usr/games/cowsay /usr/local/bin/cowsay
ENTRYPOINT ["cowsay"]
