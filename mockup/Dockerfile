FROM hbrls/eggjs:latest

RUN \
  cd /var && wget https://github.com/wechat-developer/wechat-pivot/archive/docker-mockup.tar.gz && \
  tar -zxvf /var/docker-mockup.tar.gz -C /var && rm /var/docker-mockup.tar.gz && \
  rm -r /var/app && mv /var/wechat-pivot-docker-mockup/mockup /var/app

RUN \
  mv /var/app/package-build.json /var/app-build/package.json && \
  cd /var/app-build && npm install --production --no-optional --no-package-lock && \
  mv /var/app-build/node_modules /var/app && \
  cd /var/app && npm run build && \
  rm -rf /var/app/node_modules

RUN \
  mv /var/app-run/node_modules /var/app && \
  cd /var/app && \
  npm install --production --no-optional --no-package-lock


# # npm install
# RUN \
#   buildDeps='git make g++' && \
#   apt-get update && apt-get install -y $buildDeps && \
#   cd /var/app && npm install --no-optional && npm cache clean --force && \
#   npm run build && rm -r /var/app/node_modules


# # eggjs node_modules
# RUN \
#   mv /var/app0/node_modules /var/app && \
#   cd /var/app && npm install --no-optional --production && npm cache clean --force


# RUN apt-get purge -y --auto-remove $buildDeps && rm -rf /var/lib/apt/lists/*
