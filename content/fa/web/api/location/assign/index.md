---
title: "Location: assign() method"
short-title: assign()
slug: Web/API/Location/assign
page-type: web-api-instance-method
browser-compat: api.Location.assign
---

{{ APIRef("HTML DOM") }}

متد **`assign()`** از رابط {{DOMXref("Location")}} باعث می‌شود که پنجره، سند موجود در URL مشخص‌شده را بارگذاری و نمایش دهد. پس از این جهتیابی، کاربر می‌تواند با فشار دادن دکمه «بازگشت» به صفحه‌ای که `Location.assign()` را فراخوانی کرده بود، بازگردد.

## نحو (Syntax)

```js-nolint
assign(url)
```

### پارامترها

- `url`
  - : یک رشته یا هر شیء دیگری که دارای {{Glossary("stringifier")}} باشد، مانند یک شیء {{domxref("URL")}}، حاوی URL صفحه مقصد برای جهتیابی. برای مثال، یک URL مطلق مانند `https://developer.mozilla.org/en-US/docs/Web/API/Location/reload`، یا یک URL نسبی — مانند `/Web` (فقط یک مسیر، برای جهتیابی به سند دیگری در همان مبدأ) یا `#specifications` (فقط یک رشته‌ی بخش، برای جهتیابی به بخشی از همان صفحه)، و غیره.

### استثناها (Exceptions)

- `SecurityError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که {{Glossary("origin", "مبدأ")}} اسکریپت فراخواننده متد با {{Glossary("Same-origin policy", "خط‌مشی همان‌مبدأ")}} صفحه‌ای که در ابتدا توسط شیء {{domxref("Location")}} توصیف شده است، یکسان نباشد؛ معمولاً زمانی که اسکریپت روی دامنه‌ای متفاوت میزبانی می‌شود. مرورگرها همچنین جهتیابی‌ها را محدود می‌کنند و ممکن است این خطا را پرتاب کنند، یک هشدار تولید کنند، یا اگر فراخوانی بیش از حد مکرر باشد، آن را نادیده بگیرند.
- `SyntaxError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که پارامتر `url` ارائه‌شده یک URL معتبر نباشد.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

```js
// جهتیابی به مقاله Location.reload
window.location.assign(
  "https://developer.mozilla.org/en-US/docs/Web/API/Location/reload",
);

// سپس جهتیابی به بخش Specifications آن
window.location.assign("#specifications");

// در نهایت جهتیابی به https://developer.mozilla.org/en-US/docs/Web
window.location.assign("/Web");
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("Location")}} که این متد به آن تعلق دارد.
- متدهای مشابه: {{domxref("Location.replace()")}} و {{domxref("Location.reload()")}}.