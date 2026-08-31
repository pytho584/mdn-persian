---
title: "CharacterData: length property"
short-title: length
slug: Web/API/CharacterData/length
page-type: web-api-instance-property
browser-compat: api.CharacterData.length
---

{{APIRef("DOM")}}

ویژگی فقط خواندنی **`CharacterData.length`** تعداد کاراکترهای موجود در داده‌های درون‌یافته را به صورت یک عدد صحیح مثبت برمی‌گرداند.

## مقدار

یک عدد صحیح مثبت که طول رشته {{domxref("CharacterData.data")}} را نشان می‌دهد.

## مثال

> [!NOTE]
> {{domxref("CharacterData")}} یک رابط انتزاعی است.
> مثال‌های زیر از {{domxref("Text")}} استفاده می‌کنند که یک رابط مشخص است که آن را پیاده‌سازی می‌کند.

```html
Length of the string in the <code>Text</code> node: <output></output>
```

```js
const output = document.querySelector("output");
const textNode = new Text("This text has been set using 'textNode.data'.");

output.value = textNode.length;
```

{{EmbedLiveSample("Example", "100%", 50)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}