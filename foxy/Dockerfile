FROM osrf/ros:foxy-desktop

RUN apt-get update
RUN apt-get upgrade -y

RUN apt-get install -y libgstreamer1.0-0 gstreamer1.0-plugins-base gstreamer1.0-plugins-good \
 gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-doc gstreamer1.0-tools \
 gstreamer1.0-x gstreamer1.0-alsa gstreamer1.0-gl gstreamer1.0-gtk3 gstreamer1.0-qt5 gstreamer1.0-pulseaudio \
 libgstreamer-plugins-base1.0-dev

WORKDIR /work/gscam_ws/src

RUN git clone https://github.com/clydemcqueen/gscam.git -b ros2

WORKDIR /work/gscam_ws

RUN rosdep install -y --from-paths . --ignore-src

RUN /bin/bash -c "source /opt/ros/foxy/setup.bash && colcon build"

CMD ["/bin/bash", "-c", "source install/local_setup.bash \
&& export GSCAM_CONFIG='videotestsrc pattern=snow ! video/x-raw,width=1280,height=720 ! videoconvert' \
&& ros2 run gscam gscam"]
