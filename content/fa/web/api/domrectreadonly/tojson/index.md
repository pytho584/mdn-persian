---
title: "DOMRectReadOnly: toJSON() method"
short-title: toJSON()
slug: Web/API/DOMRectReadOnly/toJSON
page-type: web-api-instance-method
browser-compat: api.DOMRectReadOnly.toJSON
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد `toJSON()` متعلق به {{domxref("DOMRectReadOnly")}}، یک نمایش {{Glossary("JSON")}} از شیء `DOMRectReadOnly` را بازمی‌گرداند.

## نحو

```js-nolint
toJSON()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء جدید که ویژگی‌های آن با مقادیر موجود در `DOMRectReadOnly`ای که متد روی آن فراخوانی شده، تنظیم شده‌اند.

## مثال‌ها

این مثال یک {{domxref("DOMRectReadOnly")}} می‌سازد که مستطیلی را در موقعیت `(10, 20)` با عرض `100` و ارتفاع `50` نشان می‌دهد. سپس برای دریافت نمایش JSON از این مستطیل، متد `toJSON()` را فراخوانی می‌کند.

```js
const rect = new DOMRectReadOnly(10, 20, 100, 50);

const rectJSON = rect.toJSON();
console.log(rectJSON);
// Output: { x: 10, y: 20, width: 100, height: 50, top: 20, right: 110, bottom: 70, left: 10 }
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}