```
---
title: "HTMLAllCollection: item() method"
short-title: item()
slug: Web/API/HTMLAllCollection/item
page-type: web-api-instance-method
browser-compat: api.HTMLAllCollection.item
---

{{APIRef("HTML DOM")}}

متد **`item()`** از رابط {{domxref("HTMLAllCollection")}} عنصری را که در مجموعه در افست مشخص‌شده قرار دارد برمی‌گرداند، یا عنصری را که ویژگی `id` یا `name` آن برابر با مقدار مشخص‌شده است.

## Syntax

```js-nolint
item(nameOrIndex)
```

### پارامترها

- `nameOrIndex`
  - : اگر این پارامتر یک عدد صحیح باشد یا رشته‌ای باشد که بتوان آن را به عدد صحیح تبدیل کرد، موقعیت {{domxref("Element")}} موردنظر را در مجموعه نشان می‌دهد. عناصر در یک `HTMLAllCollection` به همان ترتیبی که در سند منبع ظاهر می‌شوند، مرتب می‌شوند. اگر پارامتر رشته‌ای باشد که نتوان آن را به عدد صحیح تبدیل کرد، به‌عنوان `name` یا `id` عنصر موردنظر تفسیر می‌شود.

### مقدار بازگشتی

اگر `nameOrIndex` نمایانگر یک ایندکس باشد، `item()` عنصر {{domxref("Element")}} را در ایندکس مشخص‌شده برمی‌گرداند؛ اگر `nameOrIndex` کمتر از صفر یا بزرگ‌تر یا مساوی خاصیت `length` باشد، `null` برمی‌گرداند. اگر `nameOrIndex` نمایانگر یک نام باشد، `item()` همان مقداری را برمی‌گرداند که {{domxref("HTMLAllCollection/namedItem", "namedItem()")}} برمی‌گرداند.

## Specifications

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLCollection.item()")}}
```