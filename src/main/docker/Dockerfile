#
# Copyright 2018 Micro Focus or one of its affiliates.
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
# Base on the standard image provided by the Release Engineering team
#
FROM rh7-artifactory.svs.hpeswlab.net:8444/sepg/maven-jdk8-sepg:1.1.0-40

#
# Install Node.js 8.x (which includes npm)
#
RUN curl -sL https://deb.nodesource.com/setup_8.x | bash - && \
    apt-get install -y nodejs && \
    echo "Node.js version: $(node -v)" && \
    echo "NPM version: $(npm -v)"

#
# Tag the image
#
ARG BUILD_NUMBER
ARG BUILD_DATE
ARG GIT_REPO
ARG GIT_BRANCH
ARG GIT_COMMIT

LABEL Build.Number="$BUILD_NUMBER" \
      Build.Date="$BUILD_DATE" \
      Git.Repo="$GIT_REPO" \
      Git.Branch="$GIT_BRANCH" \
      Git.Commit="$GIT_COMMIT"
