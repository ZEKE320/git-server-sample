FROM alpine

RUN apk --update --no-cache add \
    sudo bash openssh tree git

ARG NAME=client
ARG UID=1000
ARG GID=1000

RUN addgroup -S -g "${GID}" "${NAME}" && \
    adduser -u "${UID}" -G "${NAME}" -D "${NAME}" &&\
    echo "$NAME ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

WORKDIR /home/${NAME}
USER $NAME

RUN echo "export PS1='\e[32m\u@\h \e[35m\t \e[34m\w\n\e[0m\$ '" >> ~/.bashrc

CMD ["/bin/bash"]
