---
title: "HTMLIFrameElement: allow property"
short-title: allow
slug: Web/API/HTMLIFrameElement/allow
page-type: web-api-instance-property
browser-compat: api.HTMLIFrameElement.allow
---

{{APIRef("HTML DOM")}}

ویژگی **`allow`** در رابط {{domxref("HTMLIFrameElement")}}، [سیاست مجوزها (Permissions Policy)](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مشخص‌شده برای این عنصر `<iframe>` را نشان می‌دهد. این سیاست تعیین می‌کند که بر اساس مبدأ (origin) درخواست، چه قابلیت‌هایی برای عنصر `<iframe>` در دسترس باشد (برای مثال دسترسی به `microphone`، `camera`، `battery`، `web-share` و غیره).

سیاست مجوزهایی که با ویژگی `allow` مشخص می‌شود، محدودیت بیشتری را بر سیاست تعیین‌شده در هدر {{HTTPHeader("Permissions-Policy")}} اعمال می‌کند و جایگزین آن نمی‌شود.

برای جزئیات بیشتر، [نحو سیاست مجوزها در `<iframe>`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy#iframes) را ببینید.

این ویژگی، ویژگی `allow` عنصر {{HTMLElement("iframe")}} را منعکس می‌کند.

## مقدار

این ویژگی یک رشته (string) است که [سیاست مجوزها](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مشخص‌شده برای این عنصر {{HTMLElement("iframe")}} را نشان می‌دهد؛ هر سیاست باید با فاصله از دیگری جدا شود.

## مثال‌ها

```html
<iframe
  id="el"
  src="https://example.com"
  allow="geolocation 'self' https://a.example.com https://b.example.com; fullscreen 'none'"></iframe>
```

```js
const el = document.getElementById("el");
console.log(el.allow); // Output: "geolocation 'self' https://a.example.com https://b.example.com; fullscreen 'none'"
```

برای مثال‌های بیشتر، [سیاست مجوزها در عنصر `<iframe>`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy#iframes) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [سیاست مجوزها](/en-US/docs/Web/HTTP/Guides/Permissions_Policy)