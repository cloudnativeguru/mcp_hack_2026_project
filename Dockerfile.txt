FROM python:3.10.19-slim
RUN apt-get update && apt-get install -y curl gnupg
RUN curl -s https://raw.githubusercontent.com/kubescape/kubescape/master/install.sh | /bin/bash
RUN apt-get install -y pipx
RUN pipx install mcp-proxy
ENV PATH="/root/.local/bin:${PATH}"
CMD ["mcp-proxy","--host=0.0.0.0","--port=8080","--pass-environment","kubescape", "mcpserver"]