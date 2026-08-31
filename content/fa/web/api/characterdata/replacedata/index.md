---
title: "CharacterData: replaceData() method"
short-title: replaceData()
slug: Web/API/CharacterData/replaceData
page-type: web-api-instance-method
browser-compat: api.CharacterData.replaceData
---

{{APIRef("DOM")}}

روش **`replaceData()`** از رابط {{domxref("CharacterData")}} تعداد مشخصی از کاراکترهای متن موجود در یک گره `CharacterData` را حذف کرده و آن کاراکترها را با متن ارائه‌شده جایگزین می‌کند.

## نحو

```js-nolint
replaceData(offset, count, data)
```

### پارامترها

- `offset`
  - : تعداد کاراکترهایی از ابتدای داده که در آن درج شود. `0` اولین کاراکتر رشته است.
- `count`
  - : تعداد کاراکترهایی که با داده ارائه‌شده جایگزین می‌شوند.
- `data`
  - : داده‌ای که درج می‌شود.

### مقدار بازگشتی

هیچ‌کدام.

### استثناها

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر `offset` یا `count` منفی باشد یا `offset` بزرگ‌تر از طول داده موجود باشد، پرتاب می‌شود.

## مثال

```html
<span>Result: </span>A long string.
```

```js
const span = document.querySelector("span");
const textNode = span.nextSibling;

textNode.replaceData(2, 4, "replaced");
```

{{EmbedLiveSample("Example", "100%", 50)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CharacterData.appendData()")}}
- {{domxref("CharacterData.deleteData()")}}
- {{domxref("CharacterData.insertData()")}}
- {{domxref("CharacterData.data")}}