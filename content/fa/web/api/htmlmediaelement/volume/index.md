---
title: "HTMLMediaElement: volume property"
short-title: volume
slug: Web/API/HTMLMediaElement/volume
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.volume
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLMediaElement.volume`** میزانی صدا را که رسانه با آن پخش می‌شود تنظیم می‌کند.

## مقدار

عددی بین ۰ و ۱ است؛ ۰ عملاً بی‌صدا و ۱ بلندترین مقدار ممکن است.

## مثال‌ها

```js
const obj = document.createElement("audio");
console.log(obj.volume); // 1
obj.volume = 0.75;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement")}}: رابطی که ویژگی `HTMLMediaElement.volume` را تعریف می‌کند
- {{domxref("HTMLMediaElement.muted")}}