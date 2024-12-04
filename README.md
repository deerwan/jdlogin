# jdlogin
#作者：小九九

sudo docker run -it \
  -p 12345:12345 \
  -w /etc/app \
  --name jdlogin \
  --restart always \
  python:3.12 bash -c "
    apt -y update && \
    apt -y install libnss3 libnspr4 libatk1.0-0 libatk-bridge2.0-0 libcups2 libdrm2 libdbus-1-3 libxkbcommon0 libxcomposite1 libxdamage1 libxfixes3 libxrandr2 libgbm1 libasound2 libatspi2.0-0 libxshmfence1 && \
    pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple && \
    python -m pip install --upgrade pip && \
    pip install pyppeteer Pillow asyncio aiohttp opencv-python-headless ddddocr quart && \
    wget https://raw.githubusercontent.com/deerwan/jdlogin/main/api.py -O /etc/app/api.py && \
    wget https://raw.githubusercontent.com/deerwan/jdlogin/main/login.py && \
    python /etc/app/api.py"
