FROM python:3.9

# change to temp dir
WORKDIR /temp

# upgrades
RUN apt update -y  && apt upgrade -y
RUN pip install --upgrade pip

RUN pip install flasgger

# install requirements first to engage docker cache
RUN wget https://raw.githubusercontent.com/LIAAD/yake/master/requirements.txt -O requirements.txt
RUN pip install -r requirements.txt

# install yake via pip
RUN pip install git+https://github.com/liaad/yake.git

# Copy server startup script
COPY ./yake-rest-api.py /temp

# Expose server port
ENV SERVER_PORT 5000
EXPOSE "$SERVER_PORT"

# set default command
CMD [ "python", "yake-rest-api.py" ]
