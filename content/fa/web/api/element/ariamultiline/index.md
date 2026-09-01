---
title: "Element: ariaMultiLine property"
short-title: ariaMultiLine
slug: Web/API/Element/ariaMultiLine
page-type: web-api-instance-property
browser-compat: api.Element.ariaMultiLine
---

{{APIRef("DOM")}}

ویژگی **`ariaMultiLine`** از رابط {{domxref("Element")}} مقدار ویژگی [`aria-multiline`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-multiline) را منعکس می‌کند که مشخص می‌کند آیا یک جعبهٔ متن چند خط ورودی می‌پذیرد یا فقط یک خط.

> [!NOTE]
> در صورت امکان، از عنصر HTML {{htmlelement("input")}} با `type="text"` یا {{htmlelement("textarea")}} استفاده کنید؛ زیرا این عناصر به‌صورت داخلی معنادار هستند و به ویژگی‌های ARIA نیاز ندارند.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`
  - : این یک جعبه متن چندخطی است.
- `"false"`
  - : این یک جعبه متن تک‌خطی است.

## مثال‌ها

در این مثال، ویژگی `aria-multiline` روی عنصری با شناسه `txtBoxInput` روی «true» تنظیم شده است که نشان می‌دهد این جعبه امکان ورود چند خط را فراهم می‌کند. با استفاده از `ariaMultiLine` مقدار را به «false» به‌روزرسانی می‌کنیم.

```html
<div id="txtboxMultilineLabel">Enter the tags for the article</div>
<div
  role="textbox"
  id="txtBoxInput"
  contenteditable="true"
  aria-multiline="true"
  aria-labelledby="txtboxMultilineLabel"
  aria-required="true"></div>
```

```js
let el = document.getElementById("txtBoxInput");
console.log(el.ariaMultiLine); // "true"
el.ariaMultiLine = "false";
console.log(el.ariaMultiLine); // "false"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [نقش textbox در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)
