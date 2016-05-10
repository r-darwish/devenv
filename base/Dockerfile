FROM opensuse:tumbleweed

RUN zypper install -y git zsh vim python python3 python-pip python3-pip htop openssh && rm -rf /var/cache/zypp
RUN git clone https://github.com/r-darwish/dcp.git /root/.dcp && /root/.dcp/install --no-emacs
RUN chsh -s /bin/zsh
RUN mkdir /root/.ssh
COPY sshd_config /etc/ssh/sshd_config
RUN mkdir /etc/ssh/keys
VOLUME /etc/ssh/keys
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
