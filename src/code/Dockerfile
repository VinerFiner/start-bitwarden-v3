FROM vaultwarden/server:latest

# 设置环境变量
ENV PERSISTENCE_NAS /mnt/start-bitwarden-v3

# 创建并初始化持久化目录
RUN set -eux; \
    if [ ! -d "$PERSISTENCE_NAS" ]; then \
        mkdir -p "$PERSISTENCE_NAS"; \
        cp -r /data "$PERSISTENCE_NAS"; \
        rm -rf /data; \
        echo "Created and initialized $PERSISTENCE_NAS"; \
    else \
        echo "Directory $PERSISTENCE_NAS already exists"; \
    fi; \
    ln -sfT "$PERSISTENCE_NAS" /data

# 复制文件（如果需要）
# COPY index.html /mnt/index.html

#END