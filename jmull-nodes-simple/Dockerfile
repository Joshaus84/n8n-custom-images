# Use pinned version (good)
FROM docker.n8n.io/n8nio/n8n:2.13.3

# Allow external modules in Code node
ENV NODE_FUNCTION_ALLOW_EXTERNAL=sharp
ENV N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true

# Switch to root to install packages
USER root

# Install ImageMagick (Debian-based now, not Alpine)
RUN apt-get update \
    && apt-get install -y imagemagick \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install sharp into n8n internal node_modules (critical for Code node)
WORKDIR /tmp
RUN npm install sharp --unsafe-perm \
    && mkdir -p /usr/local/lib/node_modules/n8n/node_modules \
    && cp -R /tmp/node_modules/sharp /usr/local/lib/node_modules/n8n/node_modules/ \
    && rm -rf /tmp/node_modules /tmp/package.json /tmp/package-lock.json

# Ensure correct permissions
RUN mkdir -p /home/node/.n8n/nodes \
    && chown -R node:node /home/node

# Switch back to node user
USER node
WORKDIR /home/node

# Install your custom/community nodes
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
