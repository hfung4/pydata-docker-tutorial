# If I run this docker file, we will run the following (in this order):
# Python base image gets pulled
# Check for updates and install pip
# Copy the requirements.txt file from the directory of my terminal ('dev-env' on my local machine) to the home directory of the container
# In the container, pip install the packages in requirements.txt and Jupyter
# Create a new system user called demo
# Switch to this user
# Set the working directory to user "demo"'s home directory
# Launch jupyter-notebook server inside the container




# Pull python 3 base image from Dockerhub
FROM python:3

# Check for updates, and install pip
RUN apt-get update && apt-get install -y python3-pip

# Copy the requirements.txt file from my local machine to the docker container
COPY requirements.txt .

# Run pip install to install packages in requirements.txt in the container
RUN pip install -r requirements.txt

# Install jupyter
RUN pip3 install jupyter

# Create a new system user called demo
# I don't want to run jupyter-notebook using the root user for security reasons
RUN useradd -ms /bin/bash demo

# Change to this new user
USER demo

# Set the container working directory to the user home folder
WORKDIR /home/demo

# Start the jupyter notebook
# ENTRYPOINT is a flavour of the CMD command
# Will run jupyter notebook command (start a new notebook) 
# after I spin up my container by default
ENTRYPOINT ["jupyter", "notebook", "--ip=0.0.0.0"]


