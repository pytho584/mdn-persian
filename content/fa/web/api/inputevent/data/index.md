---
title: "InputEvent: data property"
short-title: data
slug: Web/API/InputEvent/data
page-type: web-api-instance-property
browser-compat: api.InputEvent.data
---

{{APIRef("UI Events")}}

ویژگی فقط‌خواندنی **`data`** از رابط {{domxref("InputEvent")}}، رشته‌ای شامل نویسه‌های درج‌شده را برمی‌گرداند. اگر تغییری متنی را درج نکند — مانند زمانی که نویسه‌ها حذف می‌شوند — این مقدار ممکن است یک رشتهٔ خالی باشد.

## Value

یک رشته یا `null`. مشخصات، یک [overview](https://w3c.github.io/input-events/#overview) از مقدار این ویژگی را در حالت‌های مختلف ارائه می‌دهد.

## Examples

در مثال زیر، یک شنوندهٔ رویداد (event listener)، رویداد [input](/en-US/docs/Web/API/Element/input_event) را دریافت می‌کند. هر تغییر متنی که در عنصر {{htmlelement("input")}} رخ دهد، توسط `InputEvent.data` دریافت می‌شود و با استفاده از ویژگی [`Node.textContent`](/en-US/docs/Web/API/Node/textContent) در یک پاراگراف درج می‌شود.

```html
<p>Some text to copy and paste.</p>

<input type="text" />

<p class="result"></p>
```

```js
const editable = document.querySelector("input");
const result = document.querySelector(".result");

editable.addEventListener("input", (e) => {
  result.textContent = `Inputted text: ${e.data}`;
});
```

{{EmbedLiveSample('Examples')}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}