FROM python:3.10.14-slim-bullseye

# Install system dependencies
RUN apt-get update \
    && apt-get install -y \
       pkg-config \
       default-libmysqlclient-dev \
       gcc \
       python3-dev

#setting work directory
WORKDIR /backend
RUN command
# env variables
#prevent writing __pycache__ file to disk
ENV PYTHONUNVUFFERED 1 
# prevent buffering stdout and stderror
ENV PYTHONDONTWEITBYTECODE 1

# install dependencies
RUN pip install --upgrade pip

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt


COPY . .

RUN python manage.py migrate

CMD [ "python", "manage.py", "runserver" ]