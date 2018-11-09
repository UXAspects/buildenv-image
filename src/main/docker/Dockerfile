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
FROM rh7-artifactory.svs.hpeswlab.net:8443/sepg/maven-sepg-saas-image:1.0.0-SNAPSHOT

#
# Install Node.js 8.x (which includes npm)
#
RUN curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash - && \
    apt-get install -y nodejs && \
    echo "Node.js version: $(node -v)" && \
    echo "NPM version: $(npm -v)" && \
    mkdir /ux-aspects-scripts && \
    ( \
        cd /ux-aspects-scripts && \
        npm init --force --yes && \
        npm install @ux-aspects/ux-aspects-scripts \
    ) && \
    ln -s /ux-aspects-scripts/node_modules/\@ux-aspects/ux-aspects-scripts/bin/npm-reversion.js /usr/bin/npm-reversion

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
