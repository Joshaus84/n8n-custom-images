# Pin to a stable n8n release instead of using :latest
FROM docker.n8n.io/n8nio/n8n:2.13.3

# Allow external npm modules in Code node
# ImageMagick is NOT a Node module, so do not add it here
ENV NODE_FUNCTION_ALLOW_EXTERNAL=sharp
ENV N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true

# Work as root while installing OS packages and modules
USER root
WORKDIR /home/node

# Install ImageMagick
# n8n docs show the official image can be extended with apk
RUN apk update && apk add --no-cache imagemagick

# Install sharp into n8n's internal node_modules so the Code node can require it
# This follows the documented n8n/node_modules requirement and a current v2 workaround
WORKDIR /tmp
RUN npm install sharp --unsafe-perm \
    && mkdir -p /usr/local/lib/node_modules/n8n/node_modules \
    && cp -R /tmp/node_modules/sharp /usr/local/lib/node_modules/n8n/node_modules/ \
    && rm -rf /tmp/node_modules /tmp/package.json /tmp/package-lock.json

# Ensure node user home exists and is owned correctly
RUN mkdir -p /home/node/.n8n/nodes \
    && chown -R node:node /home/node/.n8n /home/node

# Switch back to node for runtime and community node installs
USER node
WORKDIR /home/node

# Install community nodes into ~/.n8n/nodes
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
