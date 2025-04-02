# Start from the official n8n image (use a specific version tag!)
# Find the latest or desired tag on Docker Hub: https://hub.docker.com/r/n8nio/n8n/tags
FROM n8nio/n8n:latest 
# Or better, pin a version like: FROM n8nio/n8n:1.39.1 

# Switch to root user to install global packages
USER root

# Install the mcp-server-monday package globally
# Using --unsafe-perm might be necessary depending on the package's install scripts
RUN npm install -g --unsafe-perm mcp-server-monday

# Switch back to the default node user that n8n runs as
USER node

# That's it! The rest of the n8n startup is handled by the base image's entrypoint.
# Do NOT add your own CMD or ENTRYPOINT unless you fully understand 
# how the base n8n image starts.