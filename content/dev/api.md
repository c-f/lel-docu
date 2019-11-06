---
title: "API Documentation"
date: 2019-02-11T19:30:08+10:00
draft: false
weight: 1
summary: API documentation for the golang backend
---

The following information can be extracted through the developer-console in the browser, when LeL is running.

```
JSON.stringify(lel);
```

**Note**: Good API documentation will be added in v0.0.2

```bash
{
  "base": "https://127.0.0.1:8888/",
  "graph": {
    "get": "https://127.0.0.1:8888/api/feat/graph/get"
  },
  "image": {
    "upload": "https://127.0.0.1:8888/api/feat/upload/image",
    "get": "https://127.0.0.1:8888/images"
  },
  "video": {
    "upload": "https://127.0.0.1:8888/api/feat/upload/video",
    "get": "https://127.0.0.1:8888/videos"
  },
  "notes": {
    "get": "https://127.0.0.1:8888/api/notes/get",
    "open": "https://127.0.0.1:8888/api/notes/open",
    "meta": "https://127.0.0.1:8888/api/notes/meta",
    "upload": "https://127.0.0.1:8888/api/feat/upload/md"
  },
  "core": {
    "ok": "https://127.0.0.1:8888/api/core/ok",
    "nav": "https://127.0.0.1:8888/api/core/nav",
    "folder": "https://127.0.0.1:8888/api/core/folder",
    "video": "https://127.0.0.1:8888/api/core/videos",
    "images": "https://127.0.0.1:8888/api/core/images",
    "tags": "https://127.0.0.1:8888/api/core/tags",
    "milestone": "https://127.0.0.1:8888/api/core/milestones",
    "metas": "https://127.0.0.1:8888/api/core/metas",
    "search": "https://127.0.0.1:8888/api/core/search",
    "channel": "wss://127.0.0.1:8888/api/core/channel"
  },
  "misato": {
    "search": "https://127.0.0.1:8888/api/feat/misato/search",
    "section": "https://127.0.0.1:8888/api/feat/misato"
  }
}

```
