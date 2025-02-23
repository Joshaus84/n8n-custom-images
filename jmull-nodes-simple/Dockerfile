FROM n8nio/n8n:latest

# Install sharp globally so that it is available to all parts of the container
RUN npm install -g sharp

# Post v1.0: Install additional n8n nodes.
RUN mkdir -p ~/.n8n/nodes && cd ~/.n8n/nodes && \
    npm install n8n-nodes-clicksend && \
    npm install n8n-nodes-clickuplookup && \
    npm install @ilhamakbarki/n8n-nodes-clickup && \
    npm install n8n-nodes-renamekeys-advanced && \
    npm install n8n-nodes-splitinbatches-advanced && \
    npm install n8n-nodes-text-manipulation && \
    npm install n8n-nodes-clickup-search && \
    npm install n8n-nodes-readpdfform && \
    npm install n8n-nodes-pdfkit && \
    npm install n8n-nodes-document-generator
