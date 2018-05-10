# Version: 0.0.1
FROM heroku/heroku:16

ENV APP_DIR /app
RUN mkdir -p ${APP_DIR}
WORKDIR ${APP_DIR}

# Download compiled OpenCV3
RUN curl -s -L "https://static.fountain.com/heroku16-buildpack-opencv3.4.1-v4.tar.gz" > vendor.tar.xz \
    && tar -xvf vendor.tar.xz

# Install pip and libraries
RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py \
    && python3 get-pip.py

# Install cv library
RUN pip3 install opencv-python \
    && curl https://www.python.org/static/apple-touch-icon-144x144-precomposed.png > image.png

# Use OpenCV libs
ENV LD_LIBRARY_PATH "$LD_LIBRARY_PATH:$APP_DIR/.heroku/vendor/lib"
ENV PATH "$PATH:$APP_DIR/.heroku/vendor/bin"

RUN curl https://dl.google.com/go/go1.10.1.linux-amd64.tar.gz > go1.10.1.linux-amd64.tar.gz \
    && tar -C /usr/local -xzf go1.10.1.linux-amd64.tar.gz

ENV PATH "$PATH:/usr/local/go/bin"

# Use special ENV for building GO library
ENV CGO_CPPFLAGS "-I$APP_DIR/.heroku/vendor/include"
ENV CGO_LDFLAGS "-L$APP_DIR/.heroku/vendor/lib -lopencv_core -lopencv_face -lopencv_videoio -lopencv_imgproc -lopencv_highgui -lopencv_imgcodecs -lopencv_objdetect -lopencv_features2d -lopencv_video -lopencv_dnn -lopencv_xfeatures2d -lopencv_plot -lopencv_tracking"
ENV CGO_CXXFLAGS "--std=c++1z" # --std=c++11

RUN go get -u -d gocv.io/x/gocv

CMD ["true"]
