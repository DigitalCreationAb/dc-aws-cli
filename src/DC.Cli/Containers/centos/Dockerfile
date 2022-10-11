FROM [[BASE_IMAGE]]

ARG USER_ID
ARG GROUP_ID

RUN yum install shadow-utils.x86_64 -y

RUN if getent passwd ${USER_ID} ; then deluser $(getent passwd ${USER_ID} | cut -d: -f1); fi &&\
    if getent group ${GROUP_ID} ; then delgroup ${GROUP_ID}; fi &&\
    groupadd local --gid ${GROUP_ID} &&\
    adduser -u ${USER_ID} --gid local local

RUN yum install golang -y

USER local