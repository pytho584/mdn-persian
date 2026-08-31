---
title: "CharacterData: insertData() method"
short-title: insertData()
slug: Web/API/CharacterData/insertData
page-type: web-api-instance-method
browser-compat: api.CharacterData.insertData
---

{{APIRef("DOM")}}

متد **`insertData()`** از رابط {{domxref("CharacterData")}} داده‌های ارائه‌شده را درون داده‌های فعلی گره `CharacterData`، در offset (فاصله) مشخص‌شده از ابتدای داده‌های موجود، درج می‌کند. داده‌های ارائه‌شده درون داده‌های موجود جاسازی می‌شوند.

## نحو

```js-nolint
insertData(offset, data)
```

### پارامترها

- `offset`
  - : offset عددی است که نشان‌دهنده تعداد کاراکترها از ابتدای داده‌ها برای درج داده‌های جدید است. مقدار `0` به معنای اولین کاراکتر رشته است.
- `data`
  - : داده‌ای که باید درج شود.

### مقدار بازگشتی

هیچ‌کدام.

### استثناها

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر `offset` منفی یا بزرگتر از طول داده‌های موجود باشد، پرتاب می‌شود.

## مثال

```html
<span>Result: </span>A string.
```

```js
const span = document.querySelector("span");
const textNode = span.nextSibling;

textNode.insertData(2, "long ");
```

{{EmbedLiveSample("Example", "100%", 50)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("CharacterData.appendData()")}}، {{domxref("CharacterData.deleteData()")}}، {{domxref("CharacterData.replaceData()")}}
- {{domxref("CharacterData.data")}}