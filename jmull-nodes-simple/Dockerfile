FROM docker.n8n.io/n8nio/n8n:2.13.3

# Allow sharp in Code node
ENV NODE_FUNCTION_ALLOW_EXTERNAL=sharp
ENV N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true

# Switch to root for installs
USER root
WORKDIR /home/node

# Install sharp into n8n internal modules
WORKDIR /tmp
RUN npm install sharp --unsafe-perm \
    && mkdir -p /usr/local/lib/node_modules/n8n/node_modules \
    && cp -R /tmp/node_modules/sharp /usr/local/lib/node_modules/n8n/node_modules/ \
    && rm -rf /tmp/node_modules /tmp/package.json /tmp/package-lock.json

# Fix permissions
RUN mkdir -p /home/node/.n8n/nodes \
    && chown -R node:node /home/node

# Back to node user
USER node
WORKDIR /home/node

# Install community nodes
RUN npm install --prefix /home/node/.n8n/nodes n8n-nodes-clicksend --unsafe-perm \
    && npm install --prefix /home/node/.n8n/nodes n8n-nodes-clickuplookup --unsafe-perm \
    && npm install --prefix /home/node/.n8n/nodes @ilhamakbarki/n8n-nodes-clickup --unsafe-perm \
    && npm install --prefix /home/node/.n8n/nodes n8n-nodes-renamekeys-advanced --unsafe-perm \
    && npm install --prefix /home/node/.n8n/nodes n8n-nodes-splitinbatches-advanced --unsafe-perm \
    && npm install --prefix /home/node/.n8n/nodes n8n-nodes-text-manipulation --unsafe-perm \
    && npm install --prefix /home/node/.n8n/nodes n8n-nodes-clickup-search --unsafe-perm \
    && npm install --prefix /home/node/.n8n/nodes n8n-nodes-readpdfform --unsafe-perm \
    && npm install --prefix /home/node/.n8n/nodes n8n-nodes-pdfkit --unsafe-perm \
    && npm install --prefix /home/node/.n8n/nodes n8n-nodes-document-generator --unsafe-perm
