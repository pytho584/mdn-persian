---
title: "HTMLImageElement: align property"
---

---
title: "HTMLImageElement: align property"
short-title: align
slug: Web/API/HTMLImageElement/align
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLImageElement.align
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

ویژگیِ **`align`** (منسوخ‌شده) در رابط {{domxref("HTMLImageElement")}} رشته‌ای است که نحوهٔ قرارگیری تصویر را نسبت به ظرفِ (container) آن مشخص می‌کند. این ویژگی، ویژگی محتوایی [`align`](/en-US/docs/Web/HTML/Reference/Elements/img#align) عنصر `<img>` را بازتاب می‌دهد.

در عوض باید از ویژگی CSS {{cssxref("vertical-align")}} استفاده کنید که با وجود نامش، در واقع روی تصاویر نیز کار می‌کند. همچنین می‌توانید از ویژگی {{cssxref("float")}} برای شناور کردن تصویر به سمت حاشیهٔ چپ یا راست استفاده کنید.

## مقدار

رشته‌ای که مقدار آن یکی از `top`، `middle`، `bottom`، `left` یا `right` است. برای آشنایی با معنی هر یک، به مرجع HTML [`<img>`](/en-US/docs/Web/HTML/Reference/Elements/img#align) مراجعه کنید.

## مثال‌ها

### تنظیم ویژگی align

```js example-bad
const img = new Image();
img.src = "example.png";
img.align = "top";
```

به‌جای استفاده از ویژگی منسوخ‌شدهٔ `align`، بهتر است ویژگی CSS `vertical-align` را تنظیم کنید:

```js example-good
const img = new Image();
img.src = "example.png";
img.style.verticalAlign = "top";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}