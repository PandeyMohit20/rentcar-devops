FROM node:24-bookworm-slim

WORKDIR /app

ENV NODE_ENV=production

RUN apt-get update \
    && apt-get install -y --no-install-recommends openssl \
    && rm -rf /var/lib/apt/lists/*

COPY package*.json ./

RUN npm ci

COPY prisma ./prisma

RUN npx prisma generate

RUN npm prune --omit=dev

COPY src ./src
COPY scripts ./scripts

RUN mkdir -p uploads

EXPOSE 5000

CMD ["node", "src/server.js"]
