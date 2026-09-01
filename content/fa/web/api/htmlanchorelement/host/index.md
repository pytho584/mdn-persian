---
title: "HTMLAnchorElement: host property"
short-title: host
slug: Web/API/HTMLAnchorElement/host
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.host
---

{{ApiRef("HTML DOM")}}

ویژگی **`host`** در رابط {{domxref("HTMLAnchorElement")}} یک رشته است که میزبان (host) را شامل می‌شود؛ این مقدار شامل {{domxref("HTMLAnchorElement.hostname", "hostname")}} و سپس، اگر {{glossary("port")}} در URL غیرخالی باشد، یک `":"` و به‌دنبال آن {{domxref("HTMLAnchorElement.port", "port")}} از URL است. اگر URL شامل `hostname` نباشد، این ویژگی حاوی رشتهٔ خالی `""` است.

برای اطلاعات بیشتر، {{domxref("URL.host")}} را ببینید.

## مقدار

یک رشته.

## مثال‌ها

```js
const anchor = document.createElement("a");

anchor.href = "https://developer.mozilla.org/en-US/HTMLAnchorElement";
anchor.host === "developer.mozilla.org";

anchor.href = "https://developer.mozilla.org:443/en-US/HTMLAnchorElement";
anchor.host === "developer.mozilla.org";
// The port number is not included because 443 is the scheme's default port

anchor.href = "https://developer.mozilla.org:4097/en-US/HTMLAnchorElement";
anchor.host === "developer.mozilla.org:4097";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAnchorElement")}} که این ویژگی متعلق به آن است.