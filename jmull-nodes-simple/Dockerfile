# Use the official n8n image as a base
FROM n8nio/n8n:latest

# Set the working directory to /home/node (n8n's default working directory)
WORKDIR /home/node

# Enable external modules in Code/Function nodes
ENV N8N_FUNCTION_ALLOW_EXTERNAL_MODULES=true

# Install ImageMagick (needed for conversion)
USER root
RUN apt-get update && apt-get install -y imagemagick

# Install sharp locally (if needed for other tasks) – optional
RUN npm install sharp --unsafe-perm

# Ensure the "node" user exists (create if needed)
RUN id node || adduser -D -u 1000 node

# Switch back to the default "node" user
USER node

# (Optional) Install additional custom nodes as before
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
