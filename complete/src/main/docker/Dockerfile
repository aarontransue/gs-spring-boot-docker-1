FROM aarontransue/openjdk-8-slim  # Base image for your docker conainter

MAINTAINER Aaron Transue <atransue@deloitte.com> # Maintainer name and email

ENV ENV_NAME local # spring boot default active profile
ENV BOOTAPP_JAVA_OPTS -Xms512m -Xms512m # java OPTS params
ENV LOG_PATH "/logs" # container logs directory
ENV BOOTAPP_USER="root" BOOTAPP_GROUP="root" BOOTAPP_PATH="/app.jar" # Default user and group.
ENV SERVER_PORT 8090 # Exposed port

EXPOSE $SERVER_PORT # Expose Container PORT to the host machine

COPY wrapper.sh /wrapper.sh
RUN chmod 555 /wrapper.sh

USER root
COPY maven/app.jar $BOOTAPP_PATH 

RUN chmod 555 $BOOTAPP_PATH && touch $BOOTAPP_PATH # Permission update
RUN mkdir $LOG_PATH
RUN chmod 777 $LOG_PATH && touch $LOG_PATH

USER $BOOTAPP_USR

ENTRYPOINT ("/wrapper.sh") # defining entry point for the container