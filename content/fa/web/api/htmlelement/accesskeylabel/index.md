---
title: "HTMLElement: accessKeyLabel property"
---

---
title: "HTMLElement: accessKeyLabel property"
short-title: accessKeyLabel
slug: Web/API/HTMLElement/accessKeyLabel
page-type: web-api-instance-property
browser-compat: api.HTMLElement.accessKeyLabel
---

{{ APIRef("HTML DOM") }}

ویژگی فقط‌خواندنی **`HTMLElement.accessKeyLabel`** رشته‌ای شامل کلید دسترسی تخصیص‌یافته توسط مرورگر به عنصر را برمی‌گرداند (در صورت وجود)؛ در غیر این صورت، رشته‌ای خالی برمی‌گرداند.

## مثال

### JavaScript

```js
const btn = document.getElementById("btn1");
const shortcutLabel = btn.accessKeyLabel || btn.accessKey;
btn.title += ` [${shortcutLabel.toUpperCase()}]`;

btn.onclick = () => {
  const feedback = document.createElement("output");
  feedback.textContent = "Pressed!";
  btn.insertAdjacentElement("afterend", feedback);
};
```

### HTML

```html
<button accesskey="h" title="Caption" id="btn1">Hover me</button>
```

### نتیجه

{{ EmbedLiveSample('Example') }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLElement.accessKey")}}
- ویژگی سراسری [accesskey](/en-US/docs/Web/HTML/Reference/Global_attributes/accesskey).