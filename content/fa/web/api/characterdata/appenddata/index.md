---
title: "CharacterData: appendData() method"
short-title: appendData()
slug: Web/API/CharacterData/appendData
page-type: web-api-instance-method
browser-compat: api.CharacterData.appendData
---

{{APIRef("DOM")}}

متد **`appendData()`** از رابط {{domxref("CharacterData")}} داده‌های ارائه‌شده را به انتهای داده‌های فعلی گره اضافه می‌کند.

## سینتکس

```js-nolint
appendData(data)
```

### پارامترها

- `data`
  - : داده‌ای که باید به گره فعلی اضافه شود.

### مقدار بازگشتی

هیچ.

## مثال

```html
<span>Result: </span>A text
```

```js
const span = document.querySelector("span");
const textNode = span.nextSibling;

textNode.appendData(" - appended text.");
```

{{EmbedLiveSample("Example", "100%", 50)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CharacterData.deleteData()")}}, {{domxref("CharacterData.insertData()")}}, {{domxref("CharacterData.replaceData()")}}
- {{domxref("CharacterData.data")}}