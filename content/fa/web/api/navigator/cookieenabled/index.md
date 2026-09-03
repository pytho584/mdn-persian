---
title: "Navigator: cookieEnabled property"
short-title: cookieEnabled
slug: Web/API/Navigator/cookieEnabled
page-type: web-api-instance-property
browser-compat: api.Navigator.cookieEnabled
---

{{ApiRef("HTML DOM")}}

`navigator.cookieEnabled` یک مقدار بولی (Boolean) برمی‌گرداند که نشان می‌دهد آیا کوکی‌ها فعال هستند یا خیر.

این ویژگی فقط خواندنی است.

## مقدار

یک مقدار بولی.

> [!NOTE]
> ممکن است مرورگرهای وب در برخی سناریوها از نوشتن برخی کوکی‌ها جلوگیری کنند. برای مثال، مرورگرهای مبتنی بر کروم، و همچنین برخی نسخه‌های آزمایشی فایرفاکس، اجازه ایجاد کوکی با ویژگی [`SameSite=None`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#samesitesamesite-value) را نمی‌دهند، مگر اینکه از طریق HTTPS و با ویژگی `Secure` ایجاد شده باشند.

## مثال‌ها

```js
if (!navigator.cookieEnabled) {
  // مرورگر از تنظیم کوکی‌ها پشتیبانی نمی‌کند یا از تنظیم آنها جلوگیری می‌کند.
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}