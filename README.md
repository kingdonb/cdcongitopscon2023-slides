To resolve pkgconfig errors installing the `cairo` gem:

```
sudo apt install libcairo2-dev libjpeg-dev librsvg2-dev \
  libpango1.0-dev libgif-dev build-essential libgirepository1.0-dev
export PKG_CONFIG_PATH=/usr/share/pkgconfig:/usr/lib/aarch64-linux-gnu/pkgconfig
```

(These instructions are specific to arm64 linux, I'm using Ubuntu 22.04)
