FROM maven:3.5.2-jdk-8
# FROM openjdk:8-jdk

# Install the Google Cloud SDK.
RUN echo "deb http://packages.cloud.google.com/apt cloud-sdk-jessie main" | tee /etc/apt/sources.list.d/google-cloud-sdk.list
RUN curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
RUN apt-get update && apt-get install wget unzip google-cloud-sdk google-cloud-sdk-app-engine-java -y

# Install gradle
# RUN wget https://services.gradle.org/distributions/gradle-3.4.1-bin.zip
# RUN mkdir /opt/gradle
# RUN unzip -d /opt/gradle gradle-3.4.1-bin.zip
# RUN export PATH=$PATH:/opt/gradle/gradle-3.4.1/bin

# Create app directory
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

# Bundle app source
COPY . /usr/src/app
RUN mvn install

EXPOSE 8080
CMD ["mvn appengine:run"]
