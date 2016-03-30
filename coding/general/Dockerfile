FROM centos:7

RUN echo "root:Docker!" | chpasswd
RUN yum -y update
RUN yum -y upgrade
RUN yum -y localinstall https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
RUN yum -y install bzip2 bzip2-devel sqlite sqlite-devel openssl-devel readline-devel zlib-devel vim gcc gcc-c++ gcc-gfortran htop zsh make wget curl git java-1.8.0-openjdk java-1.8.0-openjdk-devel tmux
RUN useradd -ms /bin/zsh francesco
USER francesco
WORKDIR /home/francesco
RUN git clone https://github.com/fstrozzi/dotfiles.git
RUN rm -f .zshrc
RUN ln -s dotfiles/zshrc ~/.zshrc
RUN ln -s dotfiles/zshenv ~/.zshenv
RUN ln -s dotfiles/tmux.conf ~/.tmux.conf
RUN git clone https://github.com/zsh-users/antigen.git .antigen
RUN git clone https://github.com/fstrozzi/dotvim-vundle.git ~/.vim
ENV HOME /home/francesco
RUN wget https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh
RUN chmod +x Miniconda2-latest-Linux-x86_64.sh && /bin/bash ./Miniconda2-latest-Linux-x86_64.sh -b
RUN $HOME/miniconda2/bin/conda install -y -c anaconda-cluster scala
RUN $HOME/miniconda2/bin/conda install -y -c bioconda ruby
RUN $HOME/miniconda2/bin/conda install -y -c rigge sbt
RUN curl https://raw.githubusercontent.com/n8han/conscript/master/setup.sh | sh
RUN /bin/zsh -c "$HOME/bin/cs n8han/giter8"
RUN echo 'export PATH=$HOME/bin:$PATH' >> .zshrc
EXPOSE 8888
CMD /bin/zsh
