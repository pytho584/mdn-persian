---
title: "Location: origin property"
short-title: origin
slug: Web/API/Location/origin
page-type: web-api-instance-property
browser-compat: api.Location.origin
---

{{APIRef("Location")}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`origin`** در رابط {{domxref("Location")}} رشته‌ای را بازمی‌گرداند که شامل سریال‌سازی یونیکد خاستگاه (origin) URLِ آن Location است.

ساختار دقیق این مقدار بسته به نوع URL متفاوت است:

- برای URLهایی که از طرح‌های `ftp:`، `http:`، `https:`، `ws:` و `wss:` استفاده می‌کنند، مقدار شامل {{domxref("Location.protocol", "protocol")}} و سپس `//` و پس از آن {{domxref("Location.host", "host")}} است. مانند `host`، {{domxref("Location.port", "port")}} فقط زمانی اضافه می‌شود که مقدار پیش‌فرضِ آن پروتکل نباشد.
- برای URLهایی که از طرح `file:` استفاده می‌کنند، مقدار به مرورگر بستگی دارد.
- برای URLهایی که از طرح `blob:` استفاده می‌کنند، خاستگاهِ URLِ پس از `blob:` بازگردانده می‌شود، اما فقط اگر آن URL از طرح‌های `http:`، `https:` یا `file:` استفاده کند. برای مثال، `blob:https://mozilla.org` دارای خاستگاه `https://mozilla.org` خواهد بود.

در تمام موارد دیگر، رشته `"null"` بازگردانده می‌شود.

برای اطلاعات بیشتر به {{domxref("URL.origin")}} مراجعه کنید.

## Value

یک رشته.

## Examples

```js
console.log(window.location.origin); // On this page returns 'https://developer.mozilla.org'
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [`Window.origin`](/en-US/docs/Web/API/Window/origin)
- {{Glossary("origin")}} — اصطلاح واژه‌نامه
