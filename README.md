Dockerfiles to test https://github.com/clydemcqueen/gscam on ros2.
Tested with Eloquent and Foxy.

~~~
set TEST_DISTRO=eloquent
cd $TEST_DISTRO
docker build --tag gscam:$TEST_DISTRO .
docker run gscam:$TEST_DISTRO
~~~
