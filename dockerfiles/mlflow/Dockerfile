FROM python:3.8-slim-buster

ENV PYTHONBUFFERED 1

COPY requirements.txt /
RUN pip install -r requirements.txt --no-cache-dir

RUN apt-get update && apt-get install -y netcat

COPY ./entrypoint /entrypoint
RUN sed -i 's/\r$//g' /entrypoint && chmod +x /entrypoint

COPY ./start /start
RUN sed -i 's/\r$//g' /start && chmod +x /start

ENTRYPOINT [ "/entrypoint" ]

