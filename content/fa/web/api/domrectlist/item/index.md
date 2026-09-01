---
title: "DOMRectList: item() method"
short-title: item()
slug: Web/API/DOMRectList/item
page-type: web-api-instance-method
browser-compat: api.DOMRectList.item
---

{{APIRef("Geometry Interfaces")}}

متد `item()` در {{domxref("DOMRectList")}}، {{domxref("DOMRect")}} را در ایندکس مشخص‌شده درون لیست بازمی‌گرداند، یا اگر ایندکس خارج از محدوده باشد `null` را بازمی‌گرداند.

## Syntax

```js-nolint
item(index)
```

### Parameters

- `index`
  - : یک عدد صحیح مبتنی بر صفر که موقعیت `DOMRect` را در `DOMRectList` برای بازیابی مشخص می‌کند.

### Return value

یک شیء {{domxref("DOMRect")}} در ایندکس مشخص‌شده در `DOMRectList`، یا `null` اگر ایندکس بزرگتر یا مساوی تعداد مستطیل‌های موجود در لیست باشد.

## Example

```js
const rects = document.getElementById("rects").getClientRects();
console.log(rects.length); // Number of rectangles in the DOMRectList

if (rects.length > 0) {
  console.log(rects.item(0)); // Logs the first DOMRect object
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}