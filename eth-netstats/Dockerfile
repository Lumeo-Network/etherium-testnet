FROM node:8-alpine as builder

RUN apk add --nocache git && \
    git clone https://github.com/cubedro/eth-netstats /eth-netstats

WORKDIR /eth-netstats

RUN npm install && \
    npm install -g grunt-cli && \
    grunt

FROM node:8-alpine

COPY --from=builder /eth-netstats /app

WORKDIR /app

EXPOSE 3000

LABEL traefik.enable=true
LABEL traefik.port=3000
LABEL traefik.frontend.priority=100

CMD ["npm", "start"]
