ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Install requirements for add-on
RUN apk add --no-cache git make g++ wiringpi-dev grep wget unzip

RUN sed -i "s/v[0-9.]*\/community/edge\/community/" /etc/apk/repositories \
    && apk update && apk add wiringpi

RUN git clone https://github.com/jmichault/flash_cc2531.git && \
              cd flash_cc2531 && \
              make all

# Copy data for add-on
COPY run.sh /
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
