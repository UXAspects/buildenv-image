#
# Copyright 2021 Micro Focus or one of its affiliates.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

#
# Base on the standard Maven 3.8.4 image
#
FROM maven:3.8.4-jdk-11

#
# Install Node.js (which includes npm)
#
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash - && \
    apt-get install -y nodejs && \
    echo "Node.js version: $(node -v)" && \
    npm install npm@6 -g && \
    echo "NPM version: $(npm -v)"

#
# Install Chrome (Required for automated tests)
#
RUN wget http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_83.0.4103.97-1_amd64.deb
RUN dpkg -i google-chrome-stable_83.0.4103.97-1_amd64.deb; apt-get -fy install

#
# Fetch chromedriver to save a download on every build
#
RUN curl https://chromedriver.storage.googleapis.com/83.0.4103.39/chromedriver_linux64.zip --create-dirs -o /tmp/chromedriver_linux64.zip

#
# Install Cypress Dependencies
#
RUN apt install -y libgtk2.0-0 libgtk-3-0 libgbm-dev libnotify-dev libgconf-2-4 libnss3 libxss1 libasound2 libxtst6 xauth xvfb
