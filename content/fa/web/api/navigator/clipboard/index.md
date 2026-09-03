---
title: "Navigator: clipboard property"
short-title: clipboard
slug: Web/API/Navigator/clipboard
page-type: web-api-instance-property
browser-compat: api.Navigator.clipboard
---

{{APIRef("Clipboard API")}} {{securecontext_header}}

ویژگی فقط‌خواندنی **`clipboard`** در رابط {{domxref("Navigator")}} یک شیء {{domxref("Clipboard")}} برمی‌گرداند که برای خواندن و نوشتن محتویات کلیپ‌بورد استفاده می‌شود.

این نقطه ورود به [Clipboard API](/en-US/docs/Web/API/Clipboard_API) است که می‌توان از آن برای پیاده‌سازی قابلیت‌های برش، کپی و چسباندن در یک برنامه وب استفاده کرد.

## مقدار

شیء {{domxref("Clipboard")}} که برای دسترسی به کلیپ‌بورد سیستم استفاده می‌شود.

## مثال‌ها

کد زیر از `navigator.clipboard` برای دسترسی به کلیپ‌بورد سیستم به منظور خواندن محتوای متنی از کلیپ‌بورد استفاده می‌کند.

```js
navigator.clipboard
  .readText()
  .then(
    (clipText) => (document.querySelector(".clip-text").innerText = clipText),
  );
```

این قطعه کد محتویات عنصری را که کلاس آن `"clip-text"` است با محتوای متنی کلیپ‌بورد جایگزین می‌کند.
احتمالاً این کد در یک افزونه مرورگر استفاده می‌شود که محتوای فعلی کلیپ‌بورد را نمایش می‌دهد و به‌طور خودکار به‌صورت دوره‌ای یا هنگام رویدادهای خاص به‌روزرسانی می‌شود.

اگر کلیپ‌بورد خالی باشد یا متنی نداشته باشد، محتوای عنصر `"clip-text"` پاک می‌شود.
این اتفاق به این دلیل رخ می‌دهد که {{domxref("Clipboard.readText", "readText()")}} اگر کلیپ‌بورد خالی باشد یا متنی نداشته باشد، یک رشته خالی برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}