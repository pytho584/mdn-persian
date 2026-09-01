---
title: "DOMQuad: toJSON() method"
short-title: toJSON()
slug: Web/API/DOMQuad/toJSON
page-type: web-api-instance-method
browser-compat: api.DOMQuad.toJSON
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد `toJSON()` از {{domxref("DOMQuad")}} یک نمایش {{Glossary("JSON")}} از شیء `DOMQuad` برمی‌گرداند.

## نحو

```js-nolint
toJSON()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک شیء جدید که ویژگی‌های آن مطابق با مقادیر موجود در `DOMQuad` ای که متد روی آن فراخوانی شده است، تنظیم می‌شوند.

## مثال‌ها

این مثال یک {{domxref("DOMQuad")}} با چهار شیء {{domxref("DOMPoint")}} که گوشه‌های پنجره فعلی را با مختصات صفحه نمایش نشان می‌دهند، ایجاد می‌کند و سپس آن را به JSON تبدیل می‌کند.

```js
const topLeft = new DOMPoint(window.screenX, window.screenY);
const topRight = new DOMPoint(
  window.screenX + window.innerWidth,
  window.screenY,
);
const bottomLeft = new DOMPoint(
  window.screenX,
  window.screenY + window.innerHeight,
);
const bottomRight = new DOMPoint(
  window.screenX + window.innerWidth,
  window.screenY + window.innerHeight,
);

const quad = new DOMQuad(topLeft, topRight, bottomRight, bottomLeft);

const quadJSON = quad.toJSON();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}