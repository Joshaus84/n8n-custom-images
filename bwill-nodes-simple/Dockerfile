FROM n8nio/n8n:latest
# Post v1.0:
USER root
RUN cd /usr/local/lib/node_modules/n8n && npm install n8n-nodes-clicksend --legacy-peer-deps && npm install n8n-nodes-clickuplookup --legacy-peer-deps && npm install n8n-nodes-browserless --legacy-peer-deps && npm install n8n-nodes-meilisearch --legacy-peer-deps
USER node