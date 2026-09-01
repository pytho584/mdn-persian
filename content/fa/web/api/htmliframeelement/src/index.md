---
title: "HTMLIFrameElement: src property"
short-title: src
slug: Web/API/HTMLIFrameElement/src
page-type: web-api-instance-property
browser-compat: api.HTMLIFrameElement.src
---

{{APIRef("HTML DOM")}}

خاصیت **`HTMLIFrameElement.src`** یک رشته است که منعکس‌کننده ویژگی HTML [`src`](/en-US/docs/Web/HTML/Reference/Elements/iframe#src) بوده و حاوی آدرس محتوایی است که قرار است جاسازی شود.

توجه داشته باشید که حذف برنامه‌ای ویژگی `src` یک `<iframe>` (مثلاً از طریق {{domxref("Element.removeAttribute()")}}) باعث می‌شود `about:blank` در فریم بارگذاری شود.

## مثال

```js
const iframe = document.createElement("iframe");
iframe.src = "/";
const body = document.querySelector("body");
body.appendChild(iframe); // Fetch the image using the complete URL as the referrer
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{DOMxRef("HTMLEmbedElement.src")}}
- {{DOMxRef("HTMLImageElement.src")}}
- {{DOMxRef("HTMLMediaElement.src")}}
- {{DOMxRef("HTMLScriptElement.src")}}
- {{DOMxRef("HTMLTrackElement.src")}}