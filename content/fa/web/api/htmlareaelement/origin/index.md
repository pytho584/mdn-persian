---
title: "HTMLAreaElement: origin property"
short-title: origin
slug: Web/API/HTMLAreaElement/origin
page-type: web-api-instance-property
browser-compat: api.HTMLAreaElement.origin
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنیِ **`origin`** در رابط {{domxref("HTMLAreaElement")}} رشته‌ای را برمی‌گرداند که شامل سریال‌سازی یونیکدِ مبدأِ `href` عنصر `<area>` است.

ساختار دقیق بسته به نوع URL متفاوت است:

- برای URLهایی که از طرح‌های `ftp:`، `http:`، `https:`، `ws:` و `wss:` استفاده می‌کنند، {{domxref("HTMLAnchorElement.protocol", "protocol")}} و سپس `//` و بعد از آن {{domxref("HTMLAnchorElement.host", "host")}} می‌آید. همانند `host`، {{domxref("HTMLAnchorElement.port", "port")}} فقط زمانی درج می‌شود که برای آن پروتکل مقدار پیش‌فرض نباشد.

- برای URLهایی که از طرح `file:` استفاده می‌کنند، مقدار به مرورگر بستگی دارد.

- برای URLهایی که از طرح `blob:` استفاده می‌کنند، مبدأِ URL بعد از `blob:`، اما فقط اگر آن URL از طرح‌های `http:`، `https:` یا `file:` استفاده کند. برای مثال، `blob:https://mozilla.org` دارای مبدأ `https://mozilla.org` خواهد بود.

در همه موارد دیگر، رشته‌ی `"null"` برگردانده می‌شود.

برای اطلاعات بیشتر به {{domxref("URL.origin")}} مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

```js
// An <area id="myArea" href="https://developer.mozilla.org/en-US/HTMLAreaElement"> element is in the document
const area = document.getElementById("myArea");
area.origin; // returns 'https://developer.mozilla.org'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- رابط {{domxref("HTMLAreaElement")}} که این ویژگی به آن تعلق دارد.