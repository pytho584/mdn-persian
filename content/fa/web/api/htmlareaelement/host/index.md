---
title: "HTMLAreaElement: host property"
short-title: host
slug: Web/API/HTMLAreaElement/host
page-type: web-api-instance-property
browser-compat: api.HTMLAreaElement.host
---

{{ApiRef("HTML DOM")}}

ویژگی **`host`** در رابط {{domxref("HTMLAreaElement")}} یک رشته است که شامل میزبان (host) می‌باشد، یعنی {{domxref("HTMLAreaElement.hostname", "hostname")}} و سپس، اگر {{glossary("port")}} نشانی اینترنتی (URL) غیرخالی باشد، یک `":"` و به دنبال آن {{domxref("HTMLAreaElement.port", "port")}} نشانی اینترنتی. اگر نشانی اینترنتی `hostname` نداشته باشد، این ویژگی شامل یک رشتهٔ خالی، `""`، خواهد بود.

برای اطلاعات بیشتر به {{domxref("URL.host")}} مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

```js
const area = document.createElement("area");

area.href = "https://developer.mozilla.org/en-US/HTMLAreaElement";
area.host === "developer.mozilla.org";

area.href = "https://developer.mozilla.org:443/en-US/HTMLAreaElement";
area.host === "developer.mozilla.org";
// شمارهٔ پورت درج نمی‌شود زیرا ۴۴۳ پورت پیش‌فرض پروتکل است

area.href = "https://developer.mozilla.org:4097/en-US/HTMLAreaElement";
area.host === "developer.mozilla.org:4097";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAreaElement")}} که این ویژگی به آن تعلق دارد.