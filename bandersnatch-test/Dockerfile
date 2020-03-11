FROM python:3.7

RUN mkdir /bandersnatch
RUN mkdir /conf && chmod 777 /conf
COPY src /bandersnatch/src
ADD bandersnatch.conf /etc

RUN pip install --upgrade pip setuptools wheel
RUN pip install --upgrade -r /bandersnatch/requirements.txt
RUN pip install bandersnatch>=3.6.0

CMD ["python", "/bandersnatch/src/runner.py", "3600"]

