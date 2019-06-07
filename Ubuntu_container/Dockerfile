#Use official Docker Image for Ubuntu
FROM ubuntu:latest

#add user and get working directory
RUN useradd -ms /bin/bash opsdroid
WORKDIR /home/opsdroid

#Install required programs then install opsdroid
RUN apt update && apt -y upgrade
RUN apt-get install -y python
RUN apt-get install -y python3
RUN apt-get install -y python3-pip
RUN apt-get install -y git
RUN pip3 install opsdroid
RUN apt install sudo
RUN usermod -aG sudo opsdroid
RUN echo root:ubuntu | chpasswd
RUN echo opsdroid:ubuntu | chpasswd

#set user
USER opsdroid

#add env required variables
RUN echo "export LC_ALL=C.UTF-8" >> .bashrc
RUN echo "export LANG=C.UTF-8" >> .bashrc
RUN echo "alias opsdroid='sudo opsdroid'" >> .bashrc

EXPOSE 8080

#source file
RUN . ~/.bashrc

CMD ["/bin/bash"]
