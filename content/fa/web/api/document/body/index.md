---
title: "Document: body property"
short-title: body
slug: Web/API/Document/body
page-type: web-api-instance-property
browser-compat: api.Document.body
---

{{APIRef("DOM")}}

خاصیت **`Document.body`** نمایانگر گره (node) {{HTMLElement("body")}} یا {{HTMLElement("frameset")}} سند فعلی است، یا اگر چنین عنصری وجود نداشته باشد `null` برمی‌گرداند.

## مقدار

یکی از موارد زیر:

- {{domxref("HTMLBodyElement")}}
- {{domxref("HTMLFrameSetElement")}}
- `null`

## مثال‌ها

```js
// Given this HTML: <body id="oldBodyElement"></body>
alert(document.body.id); // "oldBodyElement"

const newBodyElement = document.createElement("body");

newBodyElement.id = "newBodyElement";
document.body = newBodyElement;
alert(document.body.id); // "newBodyElement"
```

## یادداشت‌ها

`document.body` عنصری است که محتوای سند را در خود دارد. در اسناد دارای محتوای `<body>`، عنصر `<body>` را برمی‌گرداند، و در اسناد frameset، بیرونی‌ترین عنصر `<frameset>` را برمی‌گرداند.

اگرچه خاصیت `body` قابل تنظیم است، تنظیم یک body جدید روی یک سند به طور مؤثر تمام فرزندان فعلی عنصر `<body>` موجود را حذف خواهد کرد.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## همچنین ببینید

- {{domxref("document.head")}}