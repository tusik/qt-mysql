FROM rabits/qt:5.14-desktop
MAINTAINER image (image@by.cx)

RUN sudo apt-get update -qq \
    && sudo apt-get install -y -qq python3 python3-pip mysql-client libmariadbclient-dev \
    && pip3 install gcovr \
    && sudo apt-get clean
RUN cd /tmp && curl -L -O "https://download.qt.io/official_releases/qt/5.14/5.14.1/submodules/qtbase-everywhere-src-5.14.1.tar.xz" \
    && tar xvJf qtbase-everywhere-src-5.14.1.tar.xz 
RUN cd /tmp/qtbase-everywhere-src-5.14.1/src/plugins/sqldrivers \
    && qmake -- MYSQL_INCDIR="/usr/include/mysql" MYSQL_LIBDIR="/usr/lib/x86_64-linux-gnu" \
    && sudo make sub-mysql \
    && sudo make install \
    && sudo rm -rf /tmp/qtbase-everywhere-src-*

