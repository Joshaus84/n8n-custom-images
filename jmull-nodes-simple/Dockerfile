# Use the official n8n image as a base
FROM n8nio/n8n:latest

# Set the working directory to /home/node (n8n's default working directory)
WORKDIR /home/node

# Enable external modules in Code/Function nodes
ENV N8N_FUNCTION_ALLOW_EXTERNAL_MODULES=true

# Switch to root to install system dependencies
USER root

# Update apk and install ImageMagick using Alpine's package manager
RUN apk update && apk add imagemagick

# (Optional) Install sharp locally in /home/node/node_modules
RUN npm install sharp --unsafe-perm

# Ensure the "node" user exists; if not, create it with UID 1000
RUN id node || adduser -D -u 1000 node

# Switch back to the default "node" user for runtime
USER node

# Install additional custom nodes in ~/.n8n/nodes with proper permissions
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
