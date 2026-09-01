---
title: "Element: ariaOrientation property"
short-title: ariaOrientation
slug: Web/API/Element/ariaOrientation
page-type: web-api-instance-property
browser-compat: api.Element.ariaOrientation
---

{{APIRef("DOM")}}

ویژگی **`ariaOrientation`** از رابط {{domxref("Element")}} نشان‌دهنده‌ی مقدار ویژگی [`aria-orientation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation) است که مشخص می‌کند جهت‌گیری عنصر افقی، عمودی، یا نامشخص/مبهم است.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"horizontal"`
  - : عنصر افقی است.
- `"vertical"`
  - : عنصر عمودی است.
- `"undefined"`
  - : جهت‌گیری عنصر نامشخص است.

## مثال‌ها

در این مثال، ویژگی [`aria-orientation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation) روی عنصری با شناسه `handle_zoomSlider` به `"vertical"` تنظیم شده است. با استفاده از `ariaOrientation` مقدار آن را به `"horizontal"` تغییر می‌دهیم.

```html
<div
  id="handle_zoomSlider"
  role="slider"
  aria-orientation="vertical"
  aria-valuemin="0"
  aria-valuemax="17"
  aria-valuenow="14"
  tabindex="0">
  <span>11</span>
</div>
```

```js
let el = document.getElementById("handle_zoomSlider");
console.log(el.ariaOrientation); // "vertical"
el.ariaOrientation = "horizontal";
console.log(el.ariaOrientation); // "horizontal"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}