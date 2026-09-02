---
title: "Location: hostname property"
short-title: hostname
slug: Web/API/Location/hostname
page-type: web-api-instance-property
browser-compat: api.Location.hostname
---

{{ApiRef("URL API")}}

ویژگی **`hostname`** در رابط {{domxref("Location")}} یک رشته است که شامل {{glossary("domain name", "نام دامنه")}} یا {{glossary("IP address", "نشانی IP")}} نشانی اینترنتی (URL) می‌باشد. اگر نشانی اینترنتی میزبان (hostname) نداشته باشد، این ویژگی حاوی رشته خالی `""` خواهد بود. نشانی‌های IPv4 و IPv6 نرمال‌سازی می‌شوند، به عنوان مثال صفرهای ابتدایی حذف می‌شوند، و نام دامنه‌ها به [IDN](https://en.wikipedia.org/wiki/Internationalized_domain_name) تبدیل می‌شوند.

برای اطلاعات بیشتر به {{domxref("URL.hostname")}} مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

```js
console.log(window.location.hostname);
// developer.mozilla.org

const anchor = document.createElement("a");
anchor.href = "https://developer.mozilla.org:4097/";
console.log(anchor.hostname === "developer.mozilla.org");
// شماره پورت در hostname لحاظ نمی‌شود
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}