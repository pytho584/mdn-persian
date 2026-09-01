---
title: "HTMLImageElement: border property"
short-title: border
slug: Web/API/HTMLImageElement/border
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLImageElement.border
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

ویژگی _منسوخ‌شده_ **`border`** از رابط {{domxref("HTMLImageElement")}} ضخامت حاشیه‌ای را که باید دور تصویر کشیده شود، بر حسب پیکسل مشخص می‌کند. مقدار 0 (پیش‌فرض) نشان می‌دهد که هیچ حاشیه‌ای رسم نشود. این ویژگی منعکس‌کنندهٔ ویژگی محتوایی [`border`](/en-US/docs/Web/HTML/Reference/Elements/img#border) عنصر `<img>` است.

بهتر است به جای آن از ویژگی CSS {{cssxref("border")}} یا ویژگی‌های جزء آن استفاده کنید تا نه تنها ضخامت حاشیه، بلکه گزینه‌های سبک‌دهی متنوع دیگری را نیز اعمال کنید.

## مقدار

یک رشته (string) حاوی یک مقدار صحیح که ضخامت حاشیهٔ دور تصویر را بر حسب پیکسل‌های CSS مشخص می‌کند. مقدار `0` یا یک رشتهٔ خالی نشان می‌دهد که هیچ حاشیه‌ای رسم نشود. مقدار پیش‌فرض `border` برابر `0` است.

وقتی مقدار `null` به آن اختصاص داده شود، آن مقدار `null` به رشتهٔ خالی (`""`) تبدیل می‌شود، بنابراین `elt.border = null` معادل `elt.border = ""` است.

## مثال‌ها

### تنظیم ویژگی border

```js example-bad
const img = new Image();
img.src = "example.png";
img.border = "1";
```

به جای استفاده از ویژگی منسوخ‌شدهٔ `border`، از تنظیم ویژگی CSS `border` استفاده کنید:

```js example-good
const img = new Image();
img.src = "example.png";
img.style.border = "1px solid black";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}