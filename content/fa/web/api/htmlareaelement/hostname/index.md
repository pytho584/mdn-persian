---
title: "HTMLAreaElement: hostname property"
---

{{ApiRef("HTML DOM")}}

ویژگی **`hostname`** از رابط {{domxref("HTMLAreaElement")}} یک رشته است که شامل {{glossary("domain name")}} یا {{glossary("IP address")}} از URL عنصر `<area>` می‌باشد. اگر URL میزبان (hostname) نداشته باشد، این ویژگی حاوی یک رشته خالی `""` خواهد بود. آدرس‌های IPv4 و IPv6 عادی‌سازی می‌شوند، مانند حذف صفرهای پیشرو، و نام‌های دامنه به [IDN](https://en.wikipedia.org/wiki/Internationalized_domain_name) تبدیل می‌شوند.

برای اطلاعات بیشتر به {{domxref("URL.hostname")}} مراجعه کنید.

## مقدار

یک رشته شامل دامنه URL مرتبط با عنصر `area`. می‌توان از آن هم به عنوان setter و هم getter استفاده کرد.

## مثال‌ها

```html
<textarea id="log" rows="4" cols="100"></textarea>
<map name="infographic">
  <area
    id="area1"
    shape="rect"
    coords="184,6,253,27"
    href="/en-US/docs/HTMLAreaElement"
    target="_blank"
    alt="Mozilla" />
  <area
    id="area2"
    shape="circle"
    coords="130,136,60"
    href="https://coolexample.com/"
    target="_blank"
    alt="MDN" />
</map>
```

```js
// An element is in the document
const area1 = document.getElementById("area1");
const area2 = document.getElementById("area2");

const log = document.getElementById("log");
log.textContent = `area1 hostname: ${area1.hostname} \n`; // 'developer.mozilla.org'
log.textContent += `area2 hostname: ${area2.hostname}`; // 'coolexample.com'
```

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAreaElement")}} که این ویژگی به آن تعلق دارد.