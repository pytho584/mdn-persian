---
title: "HTMLTextAreaElement: disabled property"
short-title: disabled
slug: Web/API/HTMLTextAreaElement/disabled
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.disabled
---

{{ APIRef("HTML DOM") }}

ویژگی **`disabled`** در رابط {{DOMxRef("HTMLTextAreaElement")}} مشخص می‌کند که آیا این کنترل متن چندخطی غیرفعال است و نمی‌توان با آن تعامل داشت. این ویژگی منعکس‌کنندهٔ ویژگی [`disabled`](/en-US/docs/Web/HTML/Reference/Elements/textarea#autocomplete) عنصر {{htmlelement("textarea")}} است. وقتی مقدار آن `false` باشد، این `textarea` همچنان ممکن است غیرفعال باشد، اگر عنصر والد آن، مانند یک {{htmlelement("fieldset")}}، غیرفعال باشد.

## مقدار

یک مقدار بولی.

## مثال‌ها

```js
const textareaElement = document.getElementById("comment");
if (commentsDisabled) {
  textareaElement.disabled = true;
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{HTMLElement("textarea")}}
- {{DOMXref("HTMLTextAreaElement.readOnly")}}