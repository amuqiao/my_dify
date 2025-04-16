#  新建Dockerfile（原镜像基础上扩展）    
FROM svcvit/dify-sandbox-py:0.1.3


# 替换系统源（根据基础镜像版本调整）
RUN sed -i 's@deb.debian.org@mirrors.aliyun.com@g' /etc/apt/sources.list.d/debian.sources


# 配置pip镜像源
RUN pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

# 安装中文字体 和字体配置工具
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    # 浏览器核心依赖
    libnss3 \
    libnspr4 \
    libdbus-1-3 \
    libatk1.0-0 \
    libatk-bridge2.0-0 \
    libcups2 \
    libdrm2 \
    libatspi2.0-0 \
    libx11-6 \
    libxcomposite1 \
    libxdamage1 \
    libxext6 \
    libxfixes3 \
    libxrandr2 \
    libgbm1 \
    libxcb1 \
    libxkbcommon0 \
    libpango-1.0-0 \
    libcairo2 \
    libasound2 \
    # 中文字体依赖
    fonts-wqy-microhei \
    fonts-noto-cjk \
    fonts-noto-cjk-extra \
    fontconfig \  
    # 必备字体渲染工具
    libfontconfig1 \
    # 工具
    busybox-static \
    && apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# 安装 Python 库
RUN pip install -i https://pypi.tuna.tsinghua.edu.cn/simple playwright==1.42.0 

# 安装 Chromium 浏览器
RUN playwright install chromium

# 字体缓存刷新
RUN fc-cache -fv

