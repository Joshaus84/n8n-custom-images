FROM docker.n8n.io/n8nio/n8n:2.13.3

# Allow external modules
ENV NODE_FUNCTION_ALLOW_EXTERNAL=sharp
ENV N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true

# Install sharp globally for node user
USER root
WORKDIR /home/node

RUN npm install sharp

# Ensure directories exist
RUN mkdir -p /home/node/.n8n/nodes \
    && chown -R node:node /home/node

# Switch back to node
USER node
WORKDIR /home/node

# Install community nodes
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
