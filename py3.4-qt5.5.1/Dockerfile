FROM python:3.4

MAINTAINER bssthu

# Install Deps
RUN apt-get update -y -qq && \
    apt-get install -y python3-dev qt5-default && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Install SIP
RUN mkdir -p /opt/sip && \
    cd /opt/sip && \
    curl -L -o sip.tar.gz http://sourceforge.net/projects/pyqt/files/sip/sip-4.17/sip-4.17.tar.gz && \
    tar -xf sip.tar.gz && \
    cd /opt/sip/sip-* && \
    python configure.py && \
    make && \
    make install && \
    cd /opt && \
    rm -rf /opt/sip

# Install PyQt5
RUN mkdir -p /opt/pyqt && \
    cd /opt/pyqt && \
    curl -L -o pyqt5.tar.gz http://sourceforge.net/projects/pyqt/files/PyQt5/PyQt-5.5.1/PyQt-gpl-5.5.1.tar.gz
    tar -xf pyqt5.tar.gz && \
    cd /opt/pyqt/PyQt* && \
    python configure.py -c --confirm-license --no-designer-plugin -e QtCore -e QtGui -e QtWidgets && \
    make && \
    make install && \
    cd /opt && \
    rm -rf /opt/pyqt

# Check & Go to Workspace
RUN python -c "import PyQt5" && \
    mkdir -p /opt/workspace
WORKDIR /opt/workspace
