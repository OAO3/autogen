FROM python:3.11

WORKDIR /code


RUN pip install autogenstudio==0.4.0.dev45

RUN useradd -m -u 1001 user
USER user
ENV HOME=/home/user \
    PATH=/home/user/.local/bin:$PATH \
    AUTOGENSTUDIO_APPDIR=/home/user/app

WORKDIR $HOME/app

COPY --chown=user . $HOME/app

EXPOSE 8081

CMD autogenstudio ui --port 8081 --host 0.0.0.0
