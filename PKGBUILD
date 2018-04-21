# Script generated with Bloom
pkgdesc="ROS - The iot_bridge provides a bi-directional bridge between ROS and the OpenHAB Home Automation system. This allows a ROS robot to connect to a vast variety of IoT devices such as motion detectors, Z-Wave devices, lighting, door locks, etc."
url='http://wiki.ros.org/iot_bridge'

pkgname='ros-kinetic-iot-bridge'
pkgver='0.9.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
'ros-kinetic-diagnostic-msgs'
'ros-kinetic-rostest'
)

depends=('python2-requests'
'ros-kinetic-diagnostic-msgs'
'ros-kinetic-rospy'
'ros-kinetic-rostopic'
)

conflicts=()
replaces=()

_dir=iot_bridge
source=()
md5sums=()

prepare() {
    cp -R $startdir/iot_bridge $srcdir/iot_bridge
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

