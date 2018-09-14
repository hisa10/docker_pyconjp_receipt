FROM python:3.7.0-stretch
MAINTAINER Hisahiro Ohmura <hisa_x@init.tw>
ARG GIT_BRANCH="master"
ARG YEAR="2018"

RUN apt-get update && apt-get upgrade -y
RUN mkdir -p /app
WORKDIR /app
RUN git clone https://github.com/pyconjp/issue_receipt.git
WORKDIR /app/issue_receipt
RUN git checkout -f origin/$GIT_BRANCH
RUN pip install -r requirements.txt
RUN pip install gunicorn
COPY db/attendee_master_$YEAR.sqlite3 /app/issue_receipt/issueReceipt
WORKDIR /app/issue_receipt/issueReceipt
RUN python manage.py makemigrations issuing
RUN python manage.py migrate

EXPOSE 8116

WORKDIR /app/issue_receipt/issueReceipt
CMD ["gunicorn", "--pid=/var/run/gunicorn.pid", "--log-file=/var/log/issue_receipt/gunicorn.log", "--bind=0.0.0.0:8116", "issueReceipt.wsgi:application"]
