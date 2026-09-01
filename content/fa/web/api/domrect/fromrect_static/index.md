---
title: "DOMRect: fromRect() static method"
short-title: fromRect()
slug: Web/API/DOMRect/fromRect_static
page-type: web-api-static-method
browser-compat: api.DOMRect.fromRect_static
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد ایستای **`fromRect()`** از شیء {{domxref("DOMRect")}} یک شیء `DOMRect` جدید با موقعیت و ابعاد مشخص‌شده می‌سازد.

## نحو

```js-nolint
DOMRect.fromRect()
DOMRect.fromRect(rectangle)
```

### پارامترها

- `rectangle` {{optional_inline}}
  - : شیءای که موقعیت و ابعاد یک مستطیل را مشخص می‌کند. همهٔ ویژگی‌ها به‌صورت پیش‌فرض `0` هستند. ویژگی‌ها عبارت‌اند از:
    - `x`: مختصات سمت چپ مستطیل.
    - `y`: مختصات سمت بالای مستطیل.
    - `width`: عرض مستطیل.
    - `height`: ارتفاع مستطیل.

### مقدار بازگشتی

یک نمونه از {{domxref("DOMRect")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}