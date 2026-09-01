---
title: "DOMQuad: getBounds() method"
short-title: getBounds()
slug: Web/API/DOMQuad/getBounds
page-type: web-api-instance-method
browser-compat: api.DOMQuad.getBounds
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد `getBounds()` از {{domxref("DOMQuad")}} یک شیء {{domxref("DOMRect")}} برمی‌گرداند که کوچکترین مستطیلی را نشان می‌دهد که کاملاً شیء `DOMQuad` را در بر می‌گیرد.

## Syntax

```js-nolint
getBounds()
```

### Parameters

هیچکدام.

### Return value

یک {{domxref("DOMRect")}} با خصوصیات x، y، width و height که جعبه محدودکننده (bounding box) را برای `DOMQuad` بر اساس مختصات گوشه‌های آن تعریف می‌کند.

## Examples

این مثال یک {{domxref("DOMQuad")}} با چهار نقطه ایجاد می‌کند، سپس مستطیل محدودکننده آن را بازیابی می‌کند.

```js
const quad = new DOMQuad(
  { x: 40, y: 25 },
  { x: 180, y: 8 },
  { x: 210, y: 150 },
  { x: 10, y: 180 },
);

const quadBounds = quad.getBounds();
```

![یک چهارضلعی نامنظم که هیچ‌یک از اضلاع آن عمودی یا افقی نیستند. چهار گوشه آن با دایره‌های قرمز مشخص شده‌اند. دور این چهارضلعی یک مستطیل خط‌چین قرار دارد. تمام اضلاع این مستطیل عمودی یا افقی هستند و چهارضلعی را مماس می‌کنند.](./domquad.svg)

شکل یک چهارضلعی نامنظم را نشان می‌دهد که توسط یک {{domxref("DOMQuad")}} نمایش داده شده است. چهار دایره قرمز رنگ نشان‌دهنده خصوصیات {{domxref("DOMPoint")}} از `p1` تا `p4` هستند. مستطیل خط‌چین نشان‌دهنده مستطیل محدودکننده‌ای است که توسط متد `getBounds()` از {{domxref("DOMQuad")}} برگردانده شده است.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}