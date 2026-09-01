---
title: "DOMMatrixReadOnly: translate() method"
short-title: translate()
slug: Web/API/DOMMatrixReadOnly/translate
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.translate
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد `translate()` از رابط {{domxref("DOMMatrixReadOnly")}} یک ماتریس جدید ایجاد می‌کند که نتیجه اعمال یک ترجمه (translation) بر روی ماتریس اصلی است.

## نحو (Syntax)

```js-nolint
translate(translateX, translateY)
translate(translateX, translateY, translateZ)
```

### پارامترها

- `translateX`
  - : عددی که ابسیسا (مختصات x) بردار انتقال‌دهنده را نشان می‌دهد.
- `translateY`
  - : عددی که ترتیب (مختصات y) بردار انتقال‌دهنده را نشان می‌دهد.
- `translateZ` {{optional_inline}}
  - : عددی که مؤلفه z بردار انتقال‌دهنده را نشان می‌دهد. اگر ارائه نشود، پیش‌فرض آن 0 است. اگر این مقدار غیر از 0 باشد، ماتریس حاصل سه‌بعدی خواهد بود.

### مقدار بازگشتی

یک [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix) برمی‌گرداند که شامل یک ماتریس جدید است که حاصل انتقال ماتریس اصلی توسط بردار داده‌شده می‌باشد. ماتریس اصلی تغییر نمی‌کند.

اگر یک ترجمه حول محور z اعمال شود، ماتریس حاصل یک ماتریس سه‌بعدی 4x4 خواهد بود.

## مثال‌ها

این SVG شامل دو مربع، یکی قرمز و یکی آبی، هر کدام در مبدأ سند قرار دارند:

```html
<svg width="250" height="250" viewBox="0 0 50 50">
  <rect width="25" height="25" fill="red" />
  <rect id="transformed" width="25" height="25" fill="blue" />
</svg>
```

جاوااسکریپت زیر ابتدا یک ماتریس همانی (identity matrix) ایجاد می‌کند، سپس از متد `translate()` برای ایجاد یک ماتریس جدید و منتقل‌شده استفاده می‌کند — که سپس به عنوان یک `transform` به مربع آبی اعمال می‌شود. مربع قرمز در جای خود باقی می‌ماند.

```js
const matrix = new DOMMatrixReadOnly().translate(25, 25);

document
  .querySelector("#transformed")
  .setAttribute("transform", matrix.toString());
```

{{EmbedLiveSample('Examples', '250', '250')}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}