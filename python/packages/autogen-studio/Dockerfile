FROM python:3.11

WORKDIR /code

ADD https://github.com/microsoft/autogen/archive/refs/tags/v0.2.40.tar.gz /tmp/autogenstudio.tar.gz
RUN mkdir -p /tmp/autogenstudio && tar -xzf /tmp/autogenstudio.tar.gz -C /tmp/autogenstudio --strip-components=1
RUN pip install -U gunicorn /tmp/autogenstudio

RUN useradd -m -u 1001 user
USER user
ENV HOME=/home/user \
    PATH=/home/user/.local/bin:$PATH \
    AUTOGENSTUDIO_APPDIR=/home/user/app

WORKDIR $HOME/app

COPY --chown=user . $HOME/app

EXPOSE 8081

CMD autogenstudio ui --port 8081 --host 0.0.0.0
