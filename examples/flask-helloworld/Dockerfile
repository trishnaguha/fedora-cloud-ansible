FROM fedora
MAINTAINER Trishna Guha<tguha@redhat.com>

RUN dnf -y update && dnf -y install python-virtualenv && dnf clean all

RUN virtualenv venv
RUN source venv/bin/activate

RUN mkdir -p /app

COPY requirements.txt /app
WORKDIR /app

RUN pip install -r requirements.txt

COPY files/ /app/
WORKDIR /app

ENTRYPOINT ["python"]
CMD ["hello_world.py"]
