FROM alpine as build
RUN apk -U add docker

FROM sgardner/alpine-ssh-slave
LABEL maintainer="yilei.yao@docker.com"
USER root
RUN apk -U add libltdl && rm -rf /var/cache/apk/*
COPY --from=build /usr/bin/docker /usr/bin/
