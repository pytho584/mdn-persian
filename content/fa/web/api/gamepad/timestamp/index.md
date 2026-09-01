---
title: "Gamepad: timestamp property"
short-title: timestamp
slug: Web/API/Gamepad/timestamp
page-type: web-api-instance-property
browser-compat: api.Gamepad.timestamp
---

{{APIRef("Gamepad API")}}

ویژگی **`Gamepad.timestamp`** در رابط {{domxref("Gamepad")}} یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که آخرین زمان به‌روزرسانی داده‌های این گیم‌پد را نشان می‌دهد.

هدف از این ویژگی این است که به توسعه‌دهندگان امکان دهد تشخیص دهند که آیا داده‌های `axes` و `button` از سخت‌افزار به‌روزرسانی شده‌اند یا خیر. این مقدار باید نسبت به ویژگی `navigationStart` در رابط {{domxref("PerformanceTiming")}} سنجیده شود. مقادیر به‌صورت یکنواخت افزایشی هستند؛ به این معنی که می‌توان آنها را مقایسه کرد تا ترتیب به‌روزرسانی‌ها مشخص شود، زیرا مقادیر جدیدتر همیشه بزرگ‌تر یا مساوی مقادیر قدیمی‌تر هستند.

> [!NOTE]
> این ویژگی در حال حاضر در هیچ مرورگری پشتیبانی نمی‌شود.

## مقدار

یک شیء {{domxref("DOMHighResTimeStamp")}}.

## مثال‌ها

```js
const gp = navigator.getGamepads()[0];
console.log(gp.timestamp);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

[استفاده از API گیم‌پد](/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)