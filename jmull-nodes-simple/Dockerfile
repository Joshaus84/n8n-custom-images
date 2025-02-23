# Use the official n8n image as the base image
FROM n8nio/n8n:latest

# Enable external modules in Function/Code nodes
ENV N8N_FUNCTION_ALLOW_EXTERNAL_MODULES=true

# Switch to root to install local dependencies
USER root

# Install sharp locally with unsafe-perm to avoid permission issues
RUN npm install sharp --unsafe-perm

# Switch back to the default "node" user for the rest of the build
USER node

# Install additional n8n nodes in the ~/.n8n/nodes directory
RUN mkdir -p ~/.n8n/nodes && \
    npm install --prefix ~/.n8n/nodes n8n-nodes-clicksend --unsafe-perm && \
    npm install --prefix ~/.n8n/nodes n8n-nodes-clickuplookup --unsafe-perm && \
    npm install --prefix ~/.n8n/nodes @ilhamakbarki/n8n-nodes-clickup --unsafe-perm && \
    npm install --prefix ~/.n8n/nodes n8n-nodes-renamekeys-advanced --unsafe-perm && \
    npm install --prefix ~/.n8n/nodes n8n-nodes-splitinbatches-advanced --unsafe-perm && \
    npm install --prefix ~/.n8n/nodes n8n-nodes-text-manipulation --unsafe-perm && \
    npm install --prefix ~/.n8n/nodes n8n-nodes-clickup-search --unsafe-perm && \
    npm install --prefix ~/.n8n/nodes n8n-nodes-readpdfform --unsafe-perm && \
    npm install --prefix ~/.n8n/nodes n8n-nodes-pdfkit --unsafe-perm && \
    npm install --prefix ~/.n8n/nodes n8n-nodes-document-generator --unsafe-perm
