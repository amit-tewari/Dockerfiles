FROM alpine:latest AS TMUX_BUILDER

RUN apk update && apk add --virtual build-dependencies bash python curl gcc build-base wget git
ADD install-tmux.sh /install-tmux.sh
RUN /install-tmux.sh
#ADD bashrc /root/.bashrc
#ADD command /root/command
#ADD run /usr/bin/run-docker-tmux
#ADD sshd.conf /etc/supervisor/conf.d/sshd.conf

#CMD ["/usr/bin/run-docker-tmux"]

#RUN touch /usr/bin/boot-docker-tmux
FROM alpine:latest
RUN apk update && apk add ncurses-terminfo
WORKDIR /root
COPY --from=TMUX_BUILDER /root/work/tmux-static/local/bin/tmux .
