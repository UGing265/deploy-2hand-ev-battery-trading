# =========================
# 1) BUILD STAGE
# =========================
FROM node:22-alpine AS builder

WORKDIR /app
RUN corepack enable

COPY package.json pnpm-lock.yaml pnpm-workspace.yaml turbo.json ./
COPY apps/api/package.json apps/api/package.json
COPY apps/web/package.json apps/web/package.json

RUN pnpm install --frozen-lockfile

COPY . .

RUN pnpm turbo run build --filter=web...

# =========================
# 2) RUNTIME STAGE
# =========================
FROM node:22-alpine AS runner

WORKDIR /app

ENV NODE_ENV=production
ENV PORT=3000

# cần cả node_modules root để symlink pnpm hoạt động
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/apps/web ./apps/web

WORKDIR /app/apps/web

EXPOSE 3000

# dùng next trong node_modules của web app
CMD ["node", "node_modules/next/dist/bin/next", "start", "-p", "3000"]
