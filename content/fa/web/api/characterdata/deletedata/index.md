---
title: "CharacterData: deleteData() method"
short-title: deleteData()
slug: Web/API/CharacterData/deleteData
page-type: web-api-instance-method
browser-compat: api.CharacterData.deleteData
---

{{APIRef("DOM")}}

متد **`deleteData()`** از رابط {{domxref("CharacterData")}} تمام یا بخشی از داده‌ها را از این گره `CharacterData` حذف می‌کند.

## سینتکس

```js-nolint
deleteData(offset, count)
```

### پارامترها

- `offset`
  - : تعداد بایت‌هایی از ابتدای داده‌ها است که حذف از آنجا شروع می‌شود. `0` اولین کاراکتر رشته است.
- `count`
  - : تعداد بایت‌هایی که باید حذف شوند.

### مقدار بازگشتی

هیچ.

### استثناها

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر `offset` بزرگ‌تر از طول داده‌های موجود باشد، پرتاب می‌شود.

## مثال

```html
<span>Result: </span>A long string.
```

```js
const span = document.querySelector("span");
const textNode = span.nextSibling;

textNode.deleteData(1, 5);
```

{{EmbedLiveSample("Example", "100%", 50)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CharacterData.appendData()")}}, {{domxref("CharacterData.insertData()")}}, {{domxref("CharacterData.replaceData()")}}
- {{domxref("CharacterData.data")}}