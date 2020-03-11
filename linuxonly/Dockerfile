FROM python:3.6-alpine3.10

RUN apk update
# Needed to build cffi
RUN apk add python-dev build-base libffi-dev

RUN pip install pypiserver pip2pi

RUN addgroup -S -g 9898 pypiserver \
    && adduser -S -u 9898 -G pypiserver pypiserver \
    && mkdir -p /data/packages \
    && chown -R pypiserver:pypiserver /data/packages \
    # Set the setgid bit so anything added here gets associated with the
    # pypiserver group
    && chmod g+s /data/packages

RUN pip2pi /data/packages jupyter-innotater

USER pypiserver
WORKDIR /data
EXPOSE 8080
ENTRYPOINT ["pypi-server", "-p", "8080"]
CMD ["packages"]
