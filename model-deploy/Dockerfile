# Pull an image that runs flask, nginx, and python 3.6
FROM tiangolo/uwsgi-nginx-flask:python3.6

# Specify my working directory in the container
WORKDIR /app/

# Copy over requirements.txt from my local machine to /app/
COPY requirements.txt /app/

# Install packages in requirements.txt
RUN pip install -r ./requirements.txt

# Set OS level variables using ENV
# ENV <variable name> <value>
ENV ENVIRONMENT production

# Copy over "main.py" and "__init__.py" from my local machine to my working directory (app folder) in the container
COPY main.py __init__.py /app/
