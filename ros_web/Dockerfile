# Use an official Python runtime as a parent image
FROM osrf/ros:lunar-desktop-full

EXPOSE 8080
EXPOSE 9090

# Set the working directory to /app
WORKDIR /

# Install packages
RUN apt-get update && apt-get install -y \
    vim \
    tmux \
    sudo \
    psmisc \
    libopencv-dev \
    ros-lunar-tf2-tools ros-lunar-tf2-bullet \
    iproute2 iputils-ping libnss-resolve \
    libgl1-mesa-glx libgl1-mesa-dri \
    python-pip python-numpy python-matplotlib htop \
    jnettop protobuf-compiler python-pil python-lxml libxml2-dev \
    libxslt1-dev python-yaml python-docutils \
    redis-server python-redis \
    ros-lunar-rosbridge-server ros-lunar-rosbridge-suite \
    ros-lunar-move-base-msgs \
    ros-lunar-rosserial ros-lunar-rosserial-arduino && \
    rm -rf /var/lib/apt/lists/*

RUN bash -c "source /opt/ros/lunar/setup.bash ; git clone https://github.com/WSU-RAS/ras_jetson.git; cd ras_jetson/src; git submodule update --init object_detection object_detection_msgs darknet_ros cob_perception_msgs; cd .. ; catkin_make --pkg cob_perception_msgs; catkin_make --pkg darknet_ros_msgs; catkin_make --pkg object_detection_msgs"
RUN bash -c "echo 'source /ras_jetson/devel/setup.bash; roslaunch object_detection web.launch &' >> ~/.bashrc"

CMD ["/bin/bash"]
