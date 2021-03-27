---
title: Note - Getting puppeteer to work in WSL
date: "2021-02-25"
description: Quick workaround to puppeteer being unable to find chromium
slug: note-puppeteer-wsl
---

I really enjoy using WSL but you can run into some wonky bugs from time to time. Here is what I had to do to get puppeteer working:

1. Install chromium in your WSL terminal

```console
sudo apt-get install chromium-browser
```

2. Install the puppeteer npm package

```console
npm install puppeteer
```

3. When launching puppeteer, pass in the path to chromium

```javascript
const browser = await puppeteer.launch({
  executablePath: "/usr/bin/chromium-browser",
})
```

Note: if this is not working, verify this is the correct location for chromium.

```console
whereis chromium-browser
```

You may need to use a different path.

Thanks to [jumminstorage](https://github.com/junminstorage) for commenting this solution [here](https://github.com/puppeteer/puppeteer/issues/1837#issuecomment-405047723).
