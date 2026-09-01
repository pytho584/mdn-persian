---
title: "DOMPointReadOnly: toJSON() method"
short-title: toJSON()
slug: Web/API/DOMPointReadOnly/toJSON
page-type: web-api-instance-method
browser-compat: api.DOMPointReadOnly.toJSON
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد `toJSON()` از {{domxref("DOMPointReadOnly")}} شیئی برمی‌گرداند که نمایش {{Glossary("JSON")}} شیء نقطه است.

## سینتکس

```js-nolint
toJSON()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء جدید که ویژگی‌های آن با مقادیر موجود در `DOMPoint` یا `DOMPointReadOnly` که متد روی آن فراخوانده شده است، مقداردهی می‌شوند.

## مثال‌ها

این مثال یک شیء {{domxref("DOMPoint")}} می‌سازد که گوشهٔ بالا-چپ پنجرهٔ فعلی را در مختصات صفحه نمایش نشان می‌دهد، سپس آن را به JSON تبدیل می‌کند.

```js
const topLeft = new DOMPoint(window.screenX, window.screenY);

const pointJSON = topLeft.toJSON();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}