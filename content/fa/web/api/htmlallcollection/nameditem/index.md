---
title: "HTMLAllCollection: namedItem() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/HTMLAllCollection/namedItem"
short-title: namedItem()
slug: Web/API/HTMLAllCollection/namedItem
page-type: web-api-instance-method
browser-compat: api.HTMLAllCollection.namedItem
---

{{APIRef("DOM")}}

**`namedItem()`** متد مربوط به رابط {{domxref("HTMLAllCollection")}}، اولین {{domxref("Element")}} را در مجموعه برمیگرداند که ویژگی `id` یا `name` آن با نام مشخصشده مطابقت داشته باشد، یا اگر هیچ عنصری مطابقت نداشت، `null` برمیگرداند.

## نحو (Syntax)

```js-nolint
namedItem(name)
```

### پارامترها

- `name`
  - : یک رشته (string) که مقدار ویژگی `id` یا `name` عنصر مورد نظر ما را نشان میدهد.

### مقدار بازگشتی

اولین {{domxref("Element")}} در {{domxref("HTMLAllCollection")}} که با `name` مطابقت دارد، یا اگر هیچکدام وجود نداشته باشد، [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}