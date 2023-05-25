FROM ubuntu:latest

ENV RUNNING_IN_DOCKER true

RUN yes | unminimize

SHELL ["bash", "-c"]

RUN groupadd -g 550 yongli \
  && useradd --create-home -u 550 -g 550 yongli

RUN apt-get update \
 && apt-get install --no-install-recommends -y \
      zsh \
      git \
      curl \
      ca-certificates \
      tmux \
      vim \
 && echo "set-option -g default-shell /bin/zsh" > /root/.tmux.conf

ENV LANG=C.UTF-8

USER yongli

RUN set -eu -o pipefail \
 && curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh | zsh -

RUN git clone https://github.com/romkatv/powerlevel10k.git /home/yongli/.oh-my-zsh/themes/powerlevel10k


# RUN sudo apt-get install --no-install-recommends -y tmux \
#  && cat /root/.zshrc | sed 's/ZSH_THEME=".*"/ZSH_THEME="agnoster"/' > /root/.zshrc_tmp \
#  && mv /root/.zshrc_tmp /root/.zshrc \
#  && echo "set-option -g default-shell /bin/zsh" > /root/.tmux.conf

# USER root

ENTRYPOINT ["zsh"]
