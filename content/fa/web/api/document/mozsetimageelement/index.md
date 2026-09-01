---
title: "Document: mozSetImageElement() method"
short-title: mozSetImageElement()
slug: Web/API/Document/mozSetImageElement
page-type: web-api-instance-method
status:
  - non-standard
browser-compat: api.Document.mozSetImageElement
---

{{ ApiRef("DOM") }}{{ non-standard_header() }}

متد **`Document.mozSetImageElement()`**، عنصری را که به‌عنوان پس‌زمینهٔ CSS برای یک پس‌زمینه با شناسهٔ عنصر پس‌زمینهٔ معین استفاده می‌شود، تغییر می‌دهد.

## سینتکس

```js-nolint
mozSetImageElement(imageElementId, imageElement)
```

### پارامترها

- `imageElementId`
  - : رشته‌ای که نام عنصری را مشخص می‌کند که به‌عنوان تصویر پس‌زمینه با استفاده از تابع CSS {{ cssxref("element", "-moz-element") }} تعیین شده است.
- `imageElement`
  - : عنصر جدیدی که به‌عنوان پس‌زمینهٔ متناظر با آن رشتهٔ عنصر تصویر استفاده می‌شود. برای حذف عنصر پس‌زمینه، `null` را مشخص کنید.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

این مثال، پس‌زمینهٔ یک بلوک {{ HTMLElement("div") }} را هر بار که کاربر روی آن کلیک می‌کند تغییر می‌دهد.

[مشاهدهٔ این مثال به‌صورت زنده](https://mdn.dev/archives/media/samples/domref/mozSetImageElement.html).

```css
#my-box {
  background-image: -moz-element(#canvas-bg);
  text-align: center;
  width: 400px;
  height: 400px;
  cursor: pointer;
}
```

CSS تعریف‌شده در بالا توسط {{HTMLElement("div")}} ما استفاده می‌شود تا عنصری با شناسهٔ «canvas-bg» را به‌عنوان پس‌زمینهٔ خود به کار گیرد.

```js
let c = 0x00;
function clicked() {
  const canvas = document.createElement("canvas");
  canvas.setAttribute("width", 100);
  canvas.setAttribute("height", 100);

  const ctx = canvas.getContext("2d");
  ctx.fillStyle = `#${c.toString(16)}0000`;
  ctx.fillRect(25, 25, 75, 75);

  c += 0x11;
  if (c > 0xff) {
    c = 0x00;
  }

  document.mozSetImageElement("canvas-bg", canvas);
}
```

کد اینجا هر بار که کاربر روی عنصر {{ HTMLElement("div") }} کلیک می‌کند فراخوانی می‌شود. یک {{ HTMLElement("canvas") }} جدید با عرض و ارتفاع 100 پیکسل ایجاد می‌کند و سپس یک مربع 50 در 50 پیکسل در آن رسم می‌کند. هر بار که این تابع فراخوانی می‌شود، مربع رنگی متفاوت دارد (مؤلفهٔ قرمز آن هر بار افزایش می‌یابد)، بنابراین هر بار که کاربر روی عنصر کلیک می‌کند، پس‌زمینه با الگوی هر چه روشن‌تری از کاشی‌های قرمز پر می‌شود.

پس از رسم بوم، `document.mozSetImageElement()` فراخوانی می‌شود تا پس‌زمینهٔ هر CSS که از شناسهٔ «canvas-bg» به‌عنوان شناسهٔ عنصر پس‌زمینه استفاده می‌کند، به بوم جدید ما تنظیم شود.

## مشخصات

بخشی از هیچ مشخصاتی نیست.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ cssxref("element", "-moz-element") }}