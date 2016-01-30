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
RUN ln -s dotfiles/zshrc ~/.zshrc
RUN ln -s dotfiles/zshenv ~/.zshenv
RUN ln -s dotfiles/tmux.conf ~/.tmux.conf
RUN git clone https://github.com/zsh-users/antigen.git .antigen
RUN curl -sSL https://raw.githubusercontent.com/fstrozzi/dotvim/master/install.sh | bash
RUN git clone https://github.com/yyuu/pyenv.git .pyenv
RUN git clone https://github.com/rbenv/ruby-build.git .rbenv/plugins/ruby-build
ENV HOME  /home/francesco
ENV PYENV_ROOT $HOME/.pyenv
ENV PATH $PYENV_ROOT/shims:$PYENV_ROOT/bin:$PATH
RUN /bin/zsh -c "pyenv install 3.5.1"
RUN /bin/zsh -c "pyenv global 3.5.1"
RUN /bin/zsh -c "pyenv rehash"
ENV PATH $HOME/.rbenv/bin:$PATH
RUN /bin/zsh -c "rbenv install 2.3.0"
RUN /bin/zsh -c "rbenv global 2.3.0"
RUN /bin/zsh -c "rbenv rehash"
RUN wget http://downloads.typesafe.com/scala/2.11.7/scala-2.11.7.tgz
RUN tar xzvf scala-2.11.7.tgz && rm -f scala-2.11.7.tgz
RUN wget https://dl.bintray.com/sbt/native-packages/sbt/0.13.9/sbt-0.13.9.tgz
RUN tar xzvf sbt-0.13.9.tgz && rm -f sbt-0.13.9.tgz
RUN curl https://raw.githubusercontent.com/n8han/conscript/master/setup.sh | sh
ENV PATH $HOME/bin:$PATH
RUN /bin/zsh -c "cs n8han/giter8"
RUN echo "export SCALA_HOME=$HOME/scala-2.11.7" >> .zshrc
RUN echo "export PATH=$HOME/scala-2.11.7/bin:$HOME/sbt/bin:$HOME/bin:$PATH" >> .zshrc
CMD /bin/zsh
