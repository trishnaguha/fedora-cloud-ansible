FROM fedora
MAINTAINER Trishna Guha<tguha@redhat.com>

RUN dnf -y update && dnf -y install python-flask python-jinja2 && dnf clean all

RUN mkdir -p /app

COPY source/ /app/
WORKDIR /app

ENTRYPOINT ["python"]
CMD ["hello_world.py"]
