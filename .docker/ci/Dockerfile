FROM ros:crystal-ros-base-bionic

MAINTAINER Lander Usategui  <lander@erlerobotics.com>

ENV ROS_DISTRO crystal

RUN apt-get update && apt-get install -y \
    python3-colcon-common-extensions \
    libboost-all-dev \
    pkg-config \
    libfcl-dev \
    libassimp-dev \
    libqhull-dev \
    ros-$ROS_DISTRO-action-msgs \
    ros-$ROS_DISTRO-resource-retriever \
    python3-vcstool \
    wget \
    && rm -rf /var/lib/apt/lists/*

# Setup ROS2 workspace
RUN mkdir -p ros2_ws/src
WORKDIR ros2_ws
RUN wget https://raw.githubusercontent.com/AcutronicRobotics/moveit2/master/external-repos.repos \
    && vcs import src < external-repos.repos
COPY ./docker-entrypoint.sh /
ENTRYPOINT ["/docker-entrypoint.sh"]
