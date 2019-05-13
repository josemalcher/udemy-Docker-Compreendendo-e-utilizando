FROM josemalcher/ubuntu-dokinf-base-ssh
MAINTAINER José Malcher Jr.<contato@josemalcher.net>

ADD issue.exemplo.net /etc/issue.exemplo.net
RUN sed -i "s/#Banner/Banner/g" /etc/ssh/sshd_config
RUN sed -i "s/issue.net/issue.exemplo.net/g" /etc/ssh/sshd_config
