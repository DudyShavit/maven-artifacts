FROM ubuntu:20.04 AS BUILD

RUN apt-get update
RUN apt install git -y
RUN  mkdir ~/artifacts
WORKDIR /root/artifacts

RUN git clone --branch master https://github.com/DudyShavit/maven-artifacts.git
# RUN cd maven-artifacts/
# RUN pwd
RUN ls ./maven-artifacts/src/assets/
#RUN git switch master
#RUN cd src/assets/
#WORKDIR /workspace
#COPY ./maven-artifacts/src/assets/*.jar .

FROM openjdk:8-jdk-slim
RUN mkdir -p /workspace
RUN useradd -u 8877 alien
# Change to non-root privilege
USER alien
COPY --from=BUILD /root/artifacts/maven-artifacts/src/assets/*.jar /workspace/
ENTRYPOINT ["bash"]