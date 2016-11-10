FROM phusion/baseimage:0.9.19

RUN echo "export EDITOR=vim" >> ~/.bashrc
RUN echo "export VISUAL=vim" >> ~/.bashrc
RUN echo "export TERM=xterm-256color">> ~/.bashrc

RUN echo 'export PS1="[ubuntu2] \[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$ "' >> /root/.bashrc

RUN rm -f /etc/service/sshd/down

# Regenerate SSH host keys. baseimage-docker does not contain any, so you
# have to do that yourself. You may also comment out this instruction; the
# init system will auto-generate one during boot.
RUN /etc/my_init.d/00_regen_ssh_host_keys.sh

COPY id_rsa_ansible.pub /tmp
RUN cat /tmp/id_rsa_ansible.pub >> ~/.ssh/authorized_keys

CMD ["/sbin/my_init"]