# Use an official Python runtime as a parent image
FROM gcr.io/tensorflow/tensorflow:latest-py3

# Set the working directory to /app
WORKDIR /notebooks

# Install packages
RUN apt-get update && apt-get install -y \
    vim \
    tmux \
    sudo \
    psmisc

# Add user
RUN useradd -ms /bin/bash -g users -G sudo garrett
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
RUN su - garrett -c "echo 'export TERM=rxvt' >> ~/.bashrc"

EXPOSE 8887

CMD ["su", "-", "garrett", "-c", "/bin/bash -c 'cd /; jupyter notebook --port=8887 --ip=127.0.0.1'"]
