
FROM docker.io/node:alpine

USER node

WORKDIR /home/node

ADD --chown=node:node package.json package-lock.json ./

RUN npm ci

ADD --chown=node:node . .

RUN npm ci --omit=dev

RUN printenv\
	&& echo $TEST_ENV

CMD ["npm", "run", "start"]

# does not seems to work
# docker build --build-arg TEST_ENV=$TEST_ENV ./sub --file ./sub/Dockerfile --tag test --no-cache

# docker build --build-arg TEST_ENV=$TEST_ENV . --tag test --no-cache