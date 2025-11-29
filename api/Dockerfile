FROM node:22-alpine

WORKDIR /app

# copy file workspace chính
COPY package.json pnpm-lock.yaml pnpm-workspace.yaml ./
RUN corepack enable

# copy full monorepo
COPY . .

# cài deps cho toàn workspace
RUN pnpm install --frozen-lockfile

# build NestJS API
RUN pnpm turbo run build --filter=api...

ENV PORT=8000
EXPOSE 8000

# nếu dist của api nằm ở apps/api/dist/main.js
CMD ["node", "apps/api/dist/main.js"]
