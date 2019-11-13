---
title: "FAQ"
date: 2019-02-11T19:30:08+10:00
draft: false
weight: 10
summary: Answers to often ask question
---

## Not possible to access LeL via the Browser

Since the transport is encrypted(https://127.0.0.1:8888) and the CA is self-signed, your browser do not trust the generated certificate.

![pic](/user/faq_firefox.png)

![pic](/user/faq_chrome.png)

### Solution

In order to trust the certificate you can import the root certificate under `$HOME/.LeL/LEL-ca.pem`

`Preference` -> `Certificates` -> `Manage Certificates` -> `Authorities` -> `import`

![pic](/user/faq_chrome-settings.png)

Afterwards the connection is trusted and the prompt will not appear again.

If you do not want to import the root-CA it is also possible to enable insecure-localhost connection in chrome:

```
chrome://flags/#allow-insecure-localhost
```

![pic](/user/faq_chrome-enable.png)
