FROM node:20-alpine3.23 AS builder
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install


FROM node:20-alpine3.23
EXPOSE 8080
RUN addgroup -S expense && adduser -S expense -G expense && \
	mkdir /opt/server && \
	chown -R expense:expense /opt/server
ENV DB_HOST="mysql"
WORKDIR /opt/server
COPY --from=builder /opt/server /opt/server
USER expense
CMD ["node","index.js"]
