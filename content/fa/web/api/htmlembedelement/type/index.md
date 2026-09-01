---
title: "HTMLEmbedElement: type property"
short-title: type
slug: Web/API/HTMLEmbedElement/type
page-type: web-api-instance-property
browser-compat: api.HTMLEmbedElement.type
---

{{APIRef("HTML DOM")}}

**خاصیت `type`** در رابط {{domxref("HTMLEmbedElement")}} رشتهای را بازمیگرداند که ویژگی `type` عنصر {{HTMLElement("embed")}} را بازتاب میدهد و {{glossary("MIME type")}} منبع را نشان میدهد. این خاصیت، مشخصه [`type`](/en-US/docs/Web/HTML/Reference/Elements/embed#type) عنصر {{htmlelement("embed")}} را منعکس میکند.

## مقدار

یک رشته؛ نوع MIME منبع.

## مثالها

```js
const el = document.getElementById("el");
console.log(el.type); // Output: "video/webp"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLObjectElement.type")}}
- {{domxref("HTMLSourceElement.type")}}
- [انواع رسانه‌های موجود در وب](/en-US/docs/Web/Media/Guides/Formats)
- [انواع MIME مهم برای توسعه‌دهندگان وب](/en-US/docs/Web/HTTP/Guides/MIME_types#important_mime_types_for_web_developers)