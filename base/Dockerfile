FROM opensuse:tumbleweed

RUN zypper install -y git zsh vim python python3 python-pip python3-pip htop openssh glibc-locale tmux && rm -rf /var/cache/zypp
RUN git clone https://github.com/r-darwish/dcp.git /root/.dcp && /root/.dcp/install --no-emacs
RUN chsh -s /bin/zsh
RUN mkdir /root/.ssh
COPY sshd_config /etc/ssh/sshd_config
RUN mkdir /etc/ssh/keys
ADD launch_sshd /sbin
RUN chmod +x /sbin/launch_sshd
VOLUME /etc/ssh/keys
EXPOSE 22
CMD ["/sbin/launch_sshd"]
