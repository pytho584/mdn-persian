---
title: "HTMLIFrameElement: name property"
short-title: name
slug: Web/API/HTMLIFrameElement/name
page-type: web-api-instance-property
browser-compat: api.HTMLIFrameElement.name
---

{{APIRef("HTML DOM")}}

ویژگی **`name`** در رابط {{domxref("HTMLIFrameElement")}} یک رشته است که ویژگی `name` عنصر {{HTMLElement("iframe")}} را بازتاب می‌دهد و نام خاص عنصر `<iframe>` را مشخص می‌کند.

## مقدار

یک رشته.

## نمونه‌ها

```html
<iframe id="el" name="example"></iframe>
```

```js
const el = document.getElementById("el");
console.log(el.name); // Output: "example"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}