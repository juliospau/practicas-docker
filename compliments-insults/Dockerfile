FROM node:current-buster-slim
WORKDIR /home/node/
COPY index.html .
COPY public/ ./public/
COPY server.js .
COPY README.md .
RUN npm init -y; npm install express
CMD ["node", "server.js"]
