# ODROID-XU4 Qt5 설치  

Qt 5 Embedded를 설치하기 위해서는 다음과 같은 절차가 필요하다.  
먼저 필요한 의존성 라이브러리들을 설치해준다.  
```    
$ sudo apt-get build-dep qt5-default
$ sudo apt-get install build-essential perl python git
```

### Libxcb
```
$ sudo apt-get install "^libxcb.*" libx11-xcb-dev libglu1-mesa-dev libxrender-dev libxi-dev
```   

다음은 Git에서 소스를 다운로드한다.  
```
$ git clone https://code.qt.io/qt/qt5.git
```


다운로드가 완료되면 현재 디렉토리에 qt5 폴더가 생성된다.  
```
$ cd qt5
$ git checkout 5.8
$ perl init-repository
$ mkdir build
~/qt5 $ sudo nano qtbase/mkspec/linux-g++/qmake.conf
```
qmake 파일을 아래와 같이 변경해준다.  
```
#
# qmake configuration for linux-g++
#

MAKEFILE_GENERATOR      = UNIX
CONFIG                 += incremental
QMAKE_INCREMENTAL_STYLE = sublib

include(../common/linux.conf)
include(../common/gcc-base-unix.conf)
include(../common/g++-unix.conf)

#QMAKE_INCDIR += /usr/include
#QMAKE_LIBDIR += /usr/lib

#QMAKE_INCDIR_OPENGL = /usr/include/GL
#QMAKE_LIBDIR_OPENGL = /usr/lib/arm-linux-gnueabihf/mesa
QMAKE_INCDIR_EGL        = /usr/include/EGL
QMAKE_LIBDIR_EGL        = /usr/lib/arm-linux-gnueabihf
QMAKE_INCDIR_OPENGL_ES2 = /usr/include/GLES2
QMAKE_LIBDIR_OPENGL_ES2 = /usr/lib/arm-linux-gnueabihf/
#QMAKE_INCDIR_OPENVG    = $QMAKE_INCDIR_EGL
#QMAKE_LIBDIR_OPENVG    = /usr/lib/arm-linux-gnueabihf/mali-egl

QMAKE_LIBS_EGL += -lEGL
#QMKAE_LIBS_GL  += -lGL
QMAKE_LIBS_OPENGL_ES2 += -lGLESv2 -lEGL

#QMAKE_LFLAGS += -Wl,-rpath-link,/usr/lib/arm-linux-gnueabihf

QMAKE_CFLAGS   +=  -mcpu=cortex-a15 -mfpu=neon-vfpv4 -mtune=cortex-a15.cortex-a7  -mfloat-abi=hard
QMAKE_CXXFLAGS += $$QMAKE_CFLAGS
QMAKE_CFLAGS_RELEASE   +=  -mcpu=cortex-a15 -mfpu=neon-vfpv4 -mtune=cortex-a15.cortex-a7 -mfloat-abi=hard
DISTRO_OPTS += "hard-float"
QMAKE_CXXFLAGS_RELEASE += $$QMAKE_CXXFLAGS -O2

QT_INSTALL_PREFIX="/home/odroid/qt5/build"  ## Edit this if you have a preference

# Preferred eglfs backend
EGLFS_DEVICE_INTEGRATION = eglfs_linuxfb
load(qt_config)
```

QMake를 생성하자.  
```
~/qt5 $ cd qtbase

~/qtbase $ ./configure -prefix "/home/odroid/qt5/build" -release -confirm-license -opensource -platform linux-g++ -opengl es2 -no-pch -qt-pcre-system-xcb -nomake tests -nomake examples
```

생성된 QMake를 빌드한다.  
```
$ sudo make -j8
$ sudo make install -j8
```

에러없이 컴파일이 완료됐다면, 정상적으로 설치가 된 것이다.  

이제 Qt Creator를 설치하면 Qt 개발환경이 구축되는 것이다.  

------------------------------------------------------------------------
