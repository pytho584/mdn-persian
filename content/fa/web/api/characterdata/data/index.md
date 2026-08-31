---
title: "CharacterData: data property"
short-title: data
slug: Web/API/CharacterData/data
page-type: web-api-instance-property
browser-compat: api.CharacterData.data
---

{{APIRef("DOM")}}

خاصیت **`data`** در رابط {{domxref("CharacterData")}} مقدار داده‌های شیء فعلی را نشان می‌دهد.

## مقدار

رشته‌ای شامل اطلاعات کاراکتری موجود در گره {{domxref("CharacterData")}}.

وقتی روی مقدار `null` تنظیم شود، آن مقدار `null` به رشته خالی (`""`) تبدیل می‌شود؛ بنابراین `cd.data = null` معادل `cd.data = ""` است.

## مثال

> [!NOTE]
> {{domxref("CharacterData")}} یک رابط انتزاعی است.
> مثال‌های زیر از دو رابط مشخص استفاده می‌کنند که آن را پیاده‌سازی کرده‌اند: {{domxref("Text")}} و {{domxref("Comment")}}.

### خواندن یک کامنت با استفاده از data

```html
<!-- This is an HTML comment -->
<output id="result"></output>
```

```js
const comment = document.body.childNodes[1];
const output = document.getElementById("result");

output.value = comment.data;
```

{{EmbedLiveSample("Reading_a_comment_using_data", "100%", 50)}}

### تنظیم محتوای یک گره متنی با استفاده از data

```html
<span>Result: </span>Not set.
```

```js
const span = document.querySelector("span");
const textNode = span.nextSibling;

textNode.data = "This text has been set using 'textNode.data'.";
```

{{EmbedLiveSample("Setting_the_content_of_a_text_node_using_data", "100%", 50)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("CharacterData.length")}} طول داده‌های موجود در گره {{domxref("CharacterData")}} را برمی‌گرداند.