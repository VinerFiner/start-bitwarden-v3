FROM vaultwarden/server:latest

## 复制文件
# COPY index.html /mnt/index.html

# 删除已存在的 /data/ 目录
RUN rm -rf /data

# 映射 本地文件到docker实例中
RUN ln -sfT /mnt/start-bitwarden-v3 /data

# END