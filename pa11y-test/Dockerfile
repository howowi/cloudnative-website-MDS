FROM buildkite/puppeteer:v1.15.0
RUN npm install --global --unsafe-perm pa11y-ci
ADD config.json /usr/config.json
ENTRYPOINT ["pa11y-ci", "-c", "/usr/config.json"]