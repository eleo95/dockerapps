FROM --platform=linux/arm64	arm64v8/node:16
#ENV DATABASE_URL="mysql://umami:umami@db:3306/umami"
ENV DATABASE_URL="postgresql://umami:umami@db:5432/umami"

#ENV DATABASE_TYPE=mysql
ENV DATABASE_TYPE=postgresql

RUN apt-get -yqq install git
RUN git clone --depth 1 --single-branch --branch master https://github.com/mikecao/umami.git /app

WORKDIR /app

RUN yarn install --frozen-lockfile
RUN yarn next telemetry disable
RUN yarn build

USER node

EXPOSE 3000
CMD ["yarn", "start"]
