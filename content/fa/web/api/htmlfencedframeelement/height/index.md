---
title: "HTMLFencedFrameElement: height property"
short-title: height
slug: Web/API/HTMLFencedFrameElement/height
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLFencedFrameElement.height
---

{{SeeCompatTable}}{{APIRef("Fenced Frame API")}}

ویژگی **`height`** در {{domxref("HTMLFencedFrameElement")}} مقدار ویژگی `height` عنصر متناظر {{htmlelement("fencedframe")}} را دریافت و تنظیم می‌کند؛ این ویژگی ارتفاع عنصر را مشخص می‌کند.

ممکن است اندازه محتوای جاسازی‌شده توسط ویژگی‌های داخلی `contentWidth` و `contentHeight` شیء {{domxref("HTMLFencedFrameElement.config", "config")}} مربوط به `<fencedframe>` تعیین شود. در چنین مواردی، تغییر {{domxref("HTMLFencedFrameElement.width", "width")}} یا `height` عنصر `<fencedframe>` اندازه ظرف جاسازی‌شده را در صفحه تغییر می‌دهد، اما سند داخل ظرف به‌صورت بصری مقیاس می‌شود تا در آن جا بگیرد. عرض و ارتفاع گزارش‌شده سند جاسازی‌شده (یعنی {{domxref("Window.innerWidth")}} و {{domxref("Window.innerHeight")}}) بدون تغییر باقی می‌مانند.

## مقدار

رشته‌ای که ارتفاع عنصر را بر حسب پیکسل CSS نشان می‌دهد. مقدار پیش‌فرض `150` است.

## مثال‌ها

```js
const frame = document.createElement("fencedframe");
frame.height = "320";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Fenced frames](https://privacysandbox.google.com/private-advertising/fenced-frame) در privacysandbox.google.com
- [The Privacy Sandbox](https://privacysandbox.google.com/) در privacysandbox.google.com