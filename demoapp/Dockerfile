FROM  python:2.7-alpine

COPY . /opt/demoapp
RUN chmod +x /opt/demoapp/server.py

RUN ls /opt/demoapp

ENTRYPOINT [ "/opt/demoapp/server.py" ]
