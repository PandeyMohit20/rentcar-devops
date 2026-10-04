FROM node:24-bookworm-slim

WORKDIR /app

ENV NODE_ENV=production

COPY package*.json ./

RUN npm ci --omit=dev

COPY prisma ./prisma

RUN npx prisma generate

COPY src ./src
COPY scripts ./scripts

RUN mkdir -p uploads

EXPOSE 5000

CMD ["node", "src/server.js"]
