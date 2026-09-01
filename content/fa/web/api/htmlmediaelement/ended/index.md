---
title: "HTMLMediaElement: ended property"
---

---
title: "HTMLMediaElement: ended property"
short-title: ended
slug: Web/API/HTMLMediaElement/ended
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.ended
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLMediaElement.ended`** نشان می‌دهد که آیا پخش رسانه در این عنصر به پایان رسیده است یا نه.

## مقدار

یک مقدار بولین (Boolean) که اگر پخشِ رسانهٔ موجود در عنصر به پایان رسیده باشد، `true` است.

اگر منبع رسانه یک {{domxref("MediaStream")}} باشد، این مقدار زمانی `true` است که مقدار ویژگی {{domxref("MediaStream.active", "active")}} جریان، `false` باشد.

## مثال‌ها

```js
const obj = document.createElement("video");
console.log(obj.ended); // false
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement")}}: رابطه‌ای که ویژگی `HTMLMediaElement.ended` را تعریف می‌کند
- {{domxref("MediaStream")}}
- {{domxref("MediaStream.active")}}