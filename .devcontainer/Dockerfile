# Use the official image as a parent image
FROM ubuntu:20.04

# Install dependencies
RUN apt-get update && apt-get install -y \
    openjdk-11-jdk \
    nodejs \
    npm \
    curl \
    git \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# Install Android SDK
RUN mkdir -p /usr/local/android-sdk-linux && cd /usr/local/android-sdk-linux && \
    curl -o sdk-tools.zip https://dl.google.com/android/repository/commandlinetools-linux-6609375_latest.zip && \
    unzip sdk-tools.zip && rm sdk-tools.zip

ENV ANDROID_SDK_ROOT /usr/local/android-sdk-linux
ENV PATH ${PATH}:${ANDROID_SDK_ROOT}/tools:${ANDROID_SDK_ROOT}/tools/bin:${ANDROID_SDK_ROOT}/platform-tools

RUN yes | sdkmanager --licenses && \
    sdkmanager "platform-tools" "platforms;android-29" "build-tools;29.0.3"

# Install React Native CLI
RUN npm install -g react-native-cli

# Set up working directory
WORKDIR /workspace
