---
title: "HTMLElement: translate property"
short-title: translate
slug: Web/API/HTMLElement/translate
page-type: web-api-instance-property
browser-compat: api.HTMLElement.translate
---

{{APIRef("HTML DOM")}}

ویژگی **`translate`** در رابط {{domxref("HTMLElement")}} مشخص می‌کند که آیا مقادیر ویژگی‌های یک عنصر و مقادیر گره‌های فرزند {{domxref("Text")}} آن هنگام بومی‌سازی صفحه ترجمه شوند یا خیر.

این ویژگی منعکس‌کننده‌ی مقدار ویژگی سراسری HTML [`translate`](/en-US/docs/Web/HTML/Reference/Global_attributes/translate) است.

## مقدار

یک مقدار بولی که اگر مقادیر ویژگی‌های یک عنصر و مقادیر گره‌های فرزند {{domxref("Text")}} آن هنگام بومی‌سازی صفحه ترجمه شوند، `true` و در غیر این صورت `false` است.

## مثال‌ها

مثال زیر نحوه فعال یا غیرفعال کردن ترجمه را از طریق اسکریپت نشان می‌دهد:

```html
<div>
  <span>The content may always be translated: </span>
  <span translate="yes">El contenido será traducido</span>
</div>
<div>
  <span id="translate-label">The content may be translated:</span>
  <span id="translate-element" translate="no">
    El contenido puede ser traducido.
  </span>
</div>
<input id="translate-controller" type="checkbox" /> Enable translation
```

```js
const label = document.getElementById("translate-label");
const element = document.getElementById("translate-element");
const controller = document.getElementById("translate-controller");

controller.addEventListener("change", (e) => {
  if (controller.checked) {
    element.translate = true;
    label.innerText = "The content may be translated:";
  } else {
    element.translate = false;
    label.innerText = "The content may not be translated:";
  }
});
```

{{EmbedLiveSample('Examples', 600, 200)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی سراسری HTML [`translate`](/en-US/docs/Web/HTML/Reference/Global_attributes/translate)