```
---
title: "HTMLMapElement: name property"
short-title: name
slug: Web/API/HTMLMapElement/name
page-type: web-api-instance-property
browser-compat: api.HTMLMapElement.name
---

{{ApiRef("HTML DOM")}}

خاصیت **`name`** از {{domxref("HTMLMapElement")}} نشان‌دهنده‌ی نام یکتای عنصر `<map>` است. مقدار این خاصیت می‌تواند با ویژگی `useMap` در عنصر {{HTMLElement("img")}} برای ارجاع به یک عنصر `<map>` استفاده شود.

اگر یک ویژگی `id` روی عنصر {{HTMLElement("map")}} تنظیم شده باشد، این خاصیت `name` باید با همان `id` یکسان باشد.

## مقدار

یک رشته‌ی غیر خالی بدون فاصله (whitespace).

## مثال

```html
<map name="image-map">
  <area shape="circle" coords="15,15,5" />
</map>
```

```js
const mapElement = document.getElementsByName("image-map")[0];
console.log(mapElement.name); // خروجی: "image-map"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- خاصیت {{domxref("HTMLImageElement.useMap")}}
- عنصر {{domxref("HTMLAreaElement")}}
```