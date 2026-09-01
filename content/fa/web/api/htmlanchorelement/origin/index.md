---
title: "HTMLAnchorElement: origin property"
---

---
title: "HTMLAnchorElement: origin property"
short-title: origin
slug: Web/API/HTMLAnchorElement/origin
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.origin
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`origin`** در واسط {{domxref("HTMLAnchorElement")}} رشته‌ای را برمی‌گرداند که شامل سریال‌سازی یونیکدِ origin (مبدأ) برای `href` عنصر `<a>` است.

ساختار دقیق آن بسته به نوع URL متفاوت است:

- برای URLهایی که از طرح‌های `ftp:`، `http:`، `https:`، `ws:` و `wss:` استفاده می‌کنند، مقدار از {{domxref("HTMLAnchorElement.protocol", "protocol")}} و سپس `//` و بعد از آن {{domxref("HTMLAnchorElement.host", "host")}} تشکیل می‌شود. مانند `host`، {{domxref("HTMLAnchorElement.port", "port")}} تنها زمانی درج می‌شود که پیش‌فرضِ آن پروتکل نباشد.
- برای URLهایی که از طرح `file:` استفاده می‌کنند، مقدار به مرورگر بستگی دارد.
- برای URLهایی که از طرح `blob:` استفاده می‌کنند، مقدار برابر با origin (مبدأ) URLِ پس از `blob:` است، اما فقط در صورتی که آن URL از طرح‌های `http:`، `https:` یا `file:` استفاده کند. برای مثال، `blob:https://mozilla.org` مقدار `https://mozilla.org` را خواهد داشت.

در تمام موارد دیگر، رشته `"null"` برگردانده می‌شود.

برای اطلاعات بیشتر به {{domxref("URL.origin")}} مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

```js
// An <a id="myAnchor" href="https://developer.mozilla.org/en-US/HTMLAnchorElement"> element is in the document
const anchor = document.getElementById("myAnchor");
anchor.origin; // returns 'https://developer.mozilla.org'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- واسط {{domxref("HTMLAnchorElement")}} که این ویژگی به آن تعلق دارد.