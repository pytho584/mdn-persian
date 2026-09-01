---

title: "HTMLSourceElement: type property"
short-title: type
slug: Web/API/HTMLSourceElement/type
page-type: web-api-instance-property
browser-compat: api.HTMLSourceElement.type

---

{{APIRef("HTML DOM")}}

ویژگی **`type`** در رابط {{domxref("HTMLSourceElement")}} یک رشته (string) است که {{glossary("MIME type","نوع MIME")}} منبع رسانه را نشان میدهد.

این ویژگی منعکسکنندهٔ ویژگی `type` عنصر {{HTMLElement("source")}} است.

## مقدار

یک رشته (string).

## مثالها

```html
<video>
  <source
    id="el"
    src="large.webp"
    type="video/webp"
    media="screen and (width >= 600px)" />
</video>
```

```js
const el = document.getElementById("el");
console.log(el.type); // Output: "video/webp"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLSourceElement.src")}}
- {{domxref("HTMLSourceElement.srcset")}}
- {{domxref("HTMLSourceElement.media")}}
- {{domxref("HTMLSourceElement.sizes")}}
- {{htmlelement("source")}}
- {{htmlelement("picture")}}
- {{htmlelement("audio")}}
- {{htmlelement("video")}}
- [انواع رسانه در وب](/en-US/docs/Web/Media/Guides/Formats)
- [انواع MIME مهم برای توسعهدهندگان وب](/en-US/docs/Web/HTTP/Guides/MIME_types#important_mime_types_for_web_developers)
- [API قابلیتهای رسانه](/en-US/docs/Web/API/Media_Capabilities_API)