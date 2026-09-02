---
title: "Location: reload() method"
short-title: reload()
slug: Web/API/Location/reload
page-type: web-api-instance-method
browser-compat: api.Location.reload
---

{{ APIRef("HTML DOM") }}

متد **`reload()`** از رابط {{DOMXref("Location")}} نشانی وب (URL) فعلی را بارگذاری مجدد می‌کند، مشابه دکمهٔ «تازه‌سازی» (Refresh).

## نحو

```js-nolint
reload()
```

### پارامترها

- `forceGet` {{non-standard_inline}}
  - : مقدار `true` را عبور دهید تا بارگذاری مجدد با دور زدن حافظهٔ نهان (cache) اجباری شود. مقدار پیش‌فرض `false` است. فقط در فایرفاکس پشتیبانی می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `SecurityError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که {{Glossary("origin")}} اسکریپت فراخوانندهٔ متد با {{Glossary("Same-origin policy", "same origin")}} صفحه‌ای که در ابتدا توسط شیء {{domxref("Location")}} توصیف شده است یکسان نباشد؛ اغلب زمانی که اسکریپت روی دامنهٔ متفاوتی میزبانی می‌شود.

## مثال‌ها

```js
// reload the current page
window.location.reload();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("Location")}} که این متد به آن تعلق دارد.
- روش‌های مشابه: {{domxref("Location.assign()")}} و
  {{domxref("Location.replace()")}}.