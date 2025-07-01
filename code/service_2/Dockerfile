FROM python:3.13-slim
WORKDIR /app
RUN apt-get update && \
    apt-get install -y curl tar && \
    rm -rf /var/lib/apt/lists/*
RUN curl -L https://github.com/astral-sh/uv/releases/latest/download/uv-x86_64-unknown-linux-gnu.tar.gz -o uv.tar.gz && \
    tar -xzf uv.tar.gz && \
    mv uv-x86_64-unknown-linux-gnu/uv /usr/local/bin/uv && \
    chmod +x /usr/local/bin/uv && \
    rm -rf uv.tar.gz uv-x86_64-unknown-linux-gnu
COPY pyproject.toml uv.lock ./
COPY app.py ./
RUN uv pip install --system .
EXPOSE 8001
CMD ["uv", "pip", "run", "flask", "--app", "app", "run", "--host=0.0.0.0", "--port=8001"]
