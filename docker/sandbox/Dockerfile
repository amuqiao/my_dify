#  新建Dockerfile（原镜像基础上扩展）    
FROM svcvit/dify-sandbox-py:0.1.3

# 安装中文字体 和字体配置工具
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    fonts-noto-cjk \
    fonts-noto-cjk-extra \
    fontconfig \  
    && apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# 添加工具层（保持基础镜像可追溯）
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    busybox-static \
    && apt-get clean

# 在最后添加字体缓存刷新
RUN fc-cache -fv

