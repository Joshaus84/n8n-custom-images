FROM docker.io/n8nio/n8n

ENV NODE_FUNCTION_ALLOW_EXTERNAL=sharp
ENV N8N_FUNCTION_ALLOW_EXTERNAL_MODULES=sharp
ENV N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true

USER root

RUN mkdir -p /home/node/.n8n/nodes \
    && chown -R node:node /home/node

USER node

WORKDIR /home/node/.n8n

RUN npm install --include=optional --os=linux --cpu=x64 sharp

WORKDIR /home/node/.n8n/nodes

RUN npm install n8n-nodes-clicksend \
    && npm install n8n-nodes-clickuplookup \
    && npm install @ilhamakbarki/n8n-nodes-clickup \
    && npm install n8n-nodes-renamekeys-advanced \
    && npm install n8n-nodes-splitinbatches-advanced \
    && npm install n8n-nodes-text-manipulation \
    && npm install n8n-nodes-clickup-search \
    && npm install n8n-nodes-readpdfform \
    && npm install n8n-nodes-pdfkit \
    && npm install n8n-nodes-document-generator

WORKDIR /home/node
