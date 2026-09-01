---
title: "HTMLInputElement: colorSpace property"
short-title: colorSpace
slug: Web/API/HTMLInputElement/colorSpace
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.colorSpace
---

{{APIRef("HTML DOM")}}

ویژگی **`colorSpace`** در رابط {{domxref("HTMLInputElement")}} منعکس‌کنندهٔ ویژگی [`colorspace`](/en-US/docs/Web/HTML/Reference/Elements/input/color#colorspace) عنصر {{HTMLElement("input")}} است، که مشخص می‌کند فضای رنگی ({{glossary("color space")}}) رنگِ CSSِ سریال‌سازی‌شده، `sRGB` (پیش‌فرض) است یا `display-p3`. این ویژگی فقط به کنترل‌های [color](/en-US/docs/Web/HTML/Reference/Elements/input/color) مربوط می‌شود.

## مقدار

رشته‌ای که مقدار ویژگی [`colorspace`](/en-US/docs/Web/HTML/Reference/Elements/input/color#colorspace) را در بر می‌گیرد.

## نمونه‌ها

### دریافت و تنظیم فضاهای رنگی

```html
<input id="color-picker" type="color" colorspace="display-p3" alpha />
```

```js
const colorInput = document.getElementById("color-picker");
console.log(colorInput.colorSpace); // "display-p3"
colorInput.colorSpace = "limited-srgb"; // convert to srgb
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [`<input type="color">`](/en-US/docs/Web/HTML/Reference/Elements/input/color)