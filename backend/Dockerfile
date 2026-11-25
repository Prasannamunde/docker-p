FROM node:20-alpine AS runtime
WORKDIR /app
ENV NODE_ENV=production

RUN addgroup -S appgroup && adduser -S appuser -G appgroup

COPY --chown=appuser:appgroup package*.json ./
RUN npm install --omit=dev && npm cache clean --force

COPY --chown=appuser:appgroup server.js ./

USER appuser

EXPOSE 4000
CMD ["node", "server.js"]
