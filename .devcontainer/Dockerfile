FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Install dependencies
RUN apt-get update && apt-get install -y \
  nodejs \
  npm \
  xfce4 \
  x11vnc \
  novnc \
  websockify \
  supervisor \
  git \
  curl \
  wget \
  && apt-get clean

# Clone the repository
RUN git clone https://github.com/dawg/dawg /workspace/dawg

WORKDIR /workspace/dawg

# Install Node.js dependencies
RUN npm install

# Expose the port for noVNC
EXPOSE 6080

# Copy the supervisor configuration
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Command to start the services
CMD ["/usr/bin/supervisord", "-n"]
