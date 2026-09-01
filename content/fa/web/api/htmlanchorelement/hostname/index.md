---
title: "HTMLAnchorElement: hostname property"
short-title: hostname
slug: Web/API/HTMLAnchorElement/hostname
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.hostname
---

{{ApiRef("HTML DOM")}}

ویژگی **`hostname`** در رابط {{domxref("HTMLAnchorElement")}} یک رشته است که شامل {{glossary("domain name")}} یا {{glossary("IP address")}} موجود در `href` عنصر `<a>` می‌باشد. اگر URL نام میزبان نداشته باشد، این ویژگی شامل یک رشته خالی، `""`، است. آدرس‌های IPv4 و IPv6 نرمال‌سازی می‌شوند، مانند حذف صفرهای ابتدایی، و نام‌های دامنه به [IDN](https://en.wikipedia.org/wiki/Internationalized_domain_name) تبدیل می‌شوند.

برای اطلاعات بیشتر به {{domxref("URL.hostname")}} مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

```js
// An <a id="myAnchor" href="/en-US/docs/HTMLAnchorElement"> element is in the document
const anchor = document.getElementById("myAnchor");
anchor.hostname; // returns 'developer.mozilla.org'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAnchorElement")}} که این ویژگی به آن تعلق دارد.