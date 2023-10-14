FROM n8nio/n8n:latest
# Post v1.0:
USER root
RUN cd /usr/local/lib/node_modules/n8n && npm install n8n-nodes-clicksend && npm install n8n-nodes-clickuplookup && npm install n8n-nodes-browserless && npm install n8n-nodes-meilisearch
USER node