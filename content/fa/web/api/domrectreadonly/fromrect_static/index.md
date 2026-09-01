---
title: "DOMRectReadOnly: fromRect() static method"
short-title: fromRect()
slug: Web/API/DOMRectReadOnly/fromRect_static
page-type: web-api-static-method
browser-compat: api.DOMRectReadOnly.fromRect_static
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد استاتیک **`fromRect()`** در شیء {{domxref("DOMRectReadOnly")}} یک شیء `DOMRectReadOnly` جدید با مکان و ابعاد مشخص‌شده ایجاد می‌کند.

## نحو (Syntax)

```js-nolint
DOMRectReadOnly.fromRect()
DOMRectReadOnly.fromRect(rectangle)
```

### پارامترها

- `rectangle` {{optional_inline}}
  - : شیئی که مکان و ابعاد یک مستطیل را مشخص می‌کند. همه ویژگی‌ها به‌صورت پیش‌فرض `0` هستند. ویژگی‌ها عبارت‌اند از:
    - `x`: مختصات سمت چپ مستطیل.
    - `y`: مختصات سمت بالای مستطیل.
    - `width`: عرض مستطیل.
    - `height`: ارتفاع مستطیل.

### مقدار بازگشتی

یک نمونه از {{domxref("DOMRectReadOnly")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}