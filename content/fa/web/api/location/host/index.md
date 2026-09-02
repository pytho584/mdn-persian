---
title: "Location: host property"
short-title: host
slug: Web/API/Location/host
page-type: web-api-instance-property
browser-compat: api.Location.host
---

{{ApiRef("Location")}}

خاصیت **`host`** در رابط {{domxref("Location")}} یک رشته است که شامل host می‌باشد، که همان {{domxref("Location.hostname", "hostname")}} است، و سپس، اگر {{glossary("port")}} URL غیرخالی باشد، یک `":"` و به دنبال آن {{domxref("Location.port", "port")}} URL قرار می‌گیرد. اگر URL دارای `hostname` نباشد، این خاصیت شامل یک رشته خالی `""` است.

برای اطلاعات بیشتر به {{domxref("URL.host")}} مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

```js
const anchor = document.createElement("a");

anchor.href = "https://developer.mozilla.org/en-US/Location.host";
console.log(anchor.host === "developer.mozilla.org");

anchor.href = "https://developer.mozilla.org:443/en-US/Location.host";
console.log(anchor.host === "developer.mozilla.org");
// The port number is not included because 443 is the scheme's default port

anchor.href = "https://developer.mozilla.org:4097/en-US/Location.host";
console.log(anchor.host === "developer.mozilla.org:4097");
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}