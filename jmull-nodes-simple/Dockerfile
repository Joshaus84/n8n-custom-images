FROM n8nio/n8n:latest

# Switch to root to install local dependencies if needed
USER root
RUN npm install sharp --unsafe-perm

# Switch back to node user
USER node

# Post v1.0: Install additional n8n nodes.
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
