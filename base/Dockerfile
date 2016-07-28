FROM fedora

RUN dnf remove -y vim-minimal && dnf install -y git zsh vim python python3 python-pip python3-pip htop openssh tmux openssh-server procps-ng emacs-nox tar --best --allowerasing && dnf clean all -y
RUN git clone https://github.com/r-darwish/dcp.git /root/.dcp && /root/.dcp/install
RUN cd /tmp && curl -L https://github.com/junegunn/fzf-bin/releases/download/0.13.3/fzf-0.13.3-linux_amd64.tgz | tar xz && mv /tmp/fzf-0.13.3-linux_amd64 /usr/local/bin/fzf
RUN curl https://raw.githubusercontent.com/junegunn/fzf/master/bin/fzf-tmux -o /usr/local/bin/fzf-tmux && chmod +x /usr/local/bin/fzf-tmux
RUN usermod -s /usr/bin/zsh root
RUN mkdir /root/.ssh
COPY sshd_config /etc/ssh/sshd_config
RUN mkdir /etc/ssh/keys
ADD launch_sshd /sbin
RUN chmod +x /sbin/launch_sshd
ENV SHELL=/usr/bin/zsh SSH_CONNECTION=1 LC_ALL=C.utf8
VOLUME /etc/ssh/keys /root/.emacs.d/elpa /root/.zplug/repos /var/cache/dnf
EXPOSE 22
CMD ["/sbin/launch_sshd"]
