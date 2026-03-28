FROM docker.n8n.io/n8nio/n8n:2.13.3

ENV NODE_FUNCTION_ALLOW_EXTERNAL=sharp
ENV N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true

USER root
WORKDIR /home/node

RUN npm install --include=optional --os=linux --cpu=x64 --libc=musl sharp

RUN mkdir -p /home/node/.n8n/nodes \
    && chown -R node:node /home/node

USER node
WORKDIR /home/node

RUN npm install --prefix /home/node/.n8n/nodes n8n-nodes-clicksend \
    && npm install --prefix /home/node/.n8n/nodes n8n-nodes-clickuplookup \
    && npm install --prefix /home/node/.n8n/nodes @ilhamakbarki/n8n-nodes-clickup \
    && npm install --prefix /home/node/.n8n/nodes n8n-nodes-renamekeys-advanced \
    && npm install --prefix /home/node/.n8n/nodes n8n-nodes-splitinbatches-advanced \
    && npm install --prefix /home/node/.n8n/nodes n8n-nodes-text-manipulation \
    && npm install --prefix /home/node/.n8n/nodes n8n-nodes-clickup-search \
    && npm install --prefix /home/node/.n8n/nodes n8n-nodes-readpdfform \
    && npm install --prefix /home/node/.n8n/nodes n8n-nodes-pdfkit \
    && npm install --prefix /home/node/.n8n/nodes n8n-nodes-document-generator
