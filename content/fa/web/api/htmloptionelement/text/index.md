---
title: "HTMLOptionElement: text property"
short-title: text
slug: Web/API/HTMLOptionElement/text
page-type: web-api-instance-property
browser-compat: api.HTMLOptionElement.text
---

{{ApiRef("HTML DOM")}}

ویژگی **`text`** از {{domxref("HTMLOptionElement")}} متنی را نشان می‌دهد که داخل عنصر {{htmlelement("option")}} قرار دارد.
این ویژگی همان اطلاعاتی را ارائه می‌دهد که {{domxref("Node.textContent")}} ارائه می‌کند.

> [!NOTE]
> اگر عنصر دارای ویژگی `label` باشد، متنی که داخل {{htmlelement("option")}} قرار دارد به صورت بصری نمایش داده نمی‌شود. در این حالت، همچنان می‌توان از ویژگی `text` برای تنظیم محتوا استفاده کرد، اما این کار هیچ اثر قابل مشاهده‌ای نخواهد داشت.

## مقدار

یک رشته (string).

## مثال

```js
const optionElement = document.getElementById("exampleOption");
console.log(`Text property: ${optionElement.text}`);
optionElement.text = "Updated text";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("select")}}
- {{HTMLElement("datalist")}}
- {{HTMLElement("optgroup")}}
- {{domxref("HTMLOptionElement.value")}}
- {{domxref("HTMLOptionElement.label")}}
- {{domxref("HTMLScriptElement.text")}}
- {{domxref("HTMLAnchorElement.text")}}