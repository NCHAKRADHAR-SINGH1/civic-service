FROM node:20-alpine

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY prisma ./prisma
RUN npx prisma generate

COPY src ./src
COPY scripts ./scripts
COPY setup-admin.js ./setup-admin.js
COPY setup-owner.js ./setup-owner.js

ENV NODE_ENV=production
EXPOSE 5000

CMD ["sh", "-c", "npm run prisma:deploy && npm start"]