# Use an official Python runtime as a parent image
FROM osrf/ros:lunar-desktop-full

# Set the working directory to /app
WORKDIR /

# Install packages
RUN apt-get update && apt-get install -y \
    vim \
    tmux \
    sudo \
    psmisc \
    libopencv-dev \
    ros-lunar-tf2-tools \
    iproute2 iputils-ping libnss-resolve \
    libgl1-mesa-glx libgl1-mesa-dri && \
    rm -rf /var/lib/apt/lists/*

# Add user
RUN useradd -ms /bin/bash -g users -G sudo garrett
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
RUN su - garrett -c "echo 'source /opt/ros/lunar/setup.bash; source /ras/catkin_ws/devel/setup.bash;' >> ~/.bashrc"
# home/back in rxvt but would cause issues in tmux
#RUN su - garrett -c "echo '[[ $TERM == xterm ]] && export TERM=rxvt' >> ~/.bashrc"

CMD ["su", "-", "garrett", "-c", "/bin/bash"]
