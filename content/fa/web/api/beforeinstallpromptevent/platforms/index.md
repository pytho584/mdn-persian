---
title: "BeforeInstallPromptEvent: platforms property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BeforeInstallPromptEvent/platforms"
translated_by: "n8n + AI"
---

---
title: "BeforeInstallPromptEvent: platforms property"
short-title: platforms
slug: Web/API/BeforeInstallPromptEvent/platforms
page-type: web-api-instance-property
status:
  - experimental
  - non-standard
browser-compat: api.BeforeInstallPromptEvent.platforms
---

{{APIRef}}{{SeeCompatTable}}{{Non-standard_header}}

**`platforms`** 属性是 {{domxref("BeforeInstallPromptEvent")}} 接口的一个属性，用于列出事件被派发的平台。该属性提供给那些希望向用户展示版本选择的用户代理（user agent），例如“web”或“play”，从而允许用户在网页版本或 Android 版本之间进行选择。

## 值

一个字符串数组，其中每个字符串标识一个安装目标平台。

## 浏览器兼容性

{{Compat}}

## 参见

- [使 PWA 可安装](/en-US/docs/Web/Progressive_web_apps/Guides/Making_PWAs_installable)
- [如何提供你自己的应用内安装体验](https://web.dev/articles/customize-install)（位于 web.dev，2021 年）