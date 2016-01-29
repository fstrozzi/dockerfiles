FROM centos:7

RUN echo "root:Docker!" | chpasswd
RUN yum -y update
RUN yum -y upgrade
RUN yum -y localinstall https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
RUN yum -y install bzip2 bzip2-devel sqlite sqlite-devel openssl-devel readline-devel zlib-devel vim gcc gcc-c++ gcc-gfortran htop zsh make wget curl git java-1.7.0-openjdk java-1.7.0-openjdk-devel tmux
RUN useradd -ms /bin/zsh francesco
USER francesco
WORKDIR /home/francesco
RUN git clone https://github.com/rbenv/rbenv.git .rbenv
RUN mkdir -p .rbenv/plugins/ruby-build
RUN git clone https://github.com/fstrozzi/dotfiles.git
RUN rm -f .zshrc
RUN ln -s dotfiles/.zshrc ~/.zshrc
RUN ln -s dotfiles/.zshenv ~/.zshenv
RUN ln -s dotfiles/.tmux.conf ~/.tmux.conf
RUN git clone https://github.com/zsh-users/antigen.git .antigen
RUN curl -sSL https://raw.githubusercontent.com/fstrozzi/dotvim/master/install.sh | bash
RUN git clone https://github.com/yyuu/pyenv.git .pyenv
RUN git clone https://github.com/rbenv/ruby-build.git .rbenv/plugins/ruby-build
#RUN source ~/.zshrc
#RUN rbenv install 2.3.0
#RUN rbenv rehash
#RUN rbenv global 2.3.0
#RUN pyenv install 3.5.1
#RUN pyenv rehash
#RUN pyenv global 3.5.1
CMD /bin/zsh
