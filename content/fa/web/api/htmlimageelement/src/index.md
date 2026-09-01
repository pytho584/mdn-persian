---
title: "HTMLImageElement: src property"
short-title: src
slug: Web/API/HTMLImageElement/src
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.src
---

{{APIRef("HTML DOM")}}

ویژگی **`src`** در رابط {{domxref("HTMLImageElement")}} تصویری را که باید در عنصر {{HTMLElement("img")}} نمایش داده شود مشخص می‌کند. این ویژگی، ویژگی محتوایی [`src`](/en-US/docs/Web/HTML/Reference/Elements/img#src) عنصر `<img>` را منعکس می‌کند.

## مقدار

یک رشته (string). برای اطلاعات بیشتر درباره نحو (syntax) ویژگی `src`، به مرجع HTML برای [`<img>`](/en-US/docs/Web/HTML/Reference/Elements/img#src) مراجعه کنید.

## مثال‌ها

### تنظیم ویژگی src

```js
const img = new Image();
img.src = "example.png";
img.alt = "An example picture";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLImageElement.currentSrc")}}
- {{domxref("HTMLImageElement.srcset")}}
- {{domxref("HTMLImageElement.sizes")}}