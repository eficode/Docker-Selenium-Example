FROM  python:alpine3.7

COPY requirements.txt /tmp/requirements.txt
RUN  pip install -r /tmp/requirements.txt

COPY tests /tests

ENTRYPOINT [ "robot" ]
