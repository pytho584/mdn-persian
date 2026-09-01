```markdown
---
title: "HTMLFencedFrameElement: width property"
short-title: width
slug: Web/API/HTMLFencedFrameElement/width
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLFencedFrameElement.width
---

{{SeeCompatTable}}{{APIRef("Fenced Frame API")}}

ویژگی **`width`** از {{domxref("HTMLFencedFrameElement")}} مقدار متناظر با ویژگی `width` عنصر {{htmlelement("fencedframe")}} را دریافت و تنظیم می‌کند که عرض عنصر را مشخص می‌کند.

اندازه محتوای جاسازی‌شده می‌تواند توسط ویژگی‌های داخلی `contentWidth` و `contentHeight` شیء {{domxref("HTMLFencedFrameElement.config", "config")}} درون `<fencedframe>` تنظیم شود. در چنین مواردی، تغییر `width` یا {{domxref("HTMLFencedFrameElement.height", "height")}} درون `<fencedframe>` اندازه ظرف جاسازی‌شده در صفحه را تغییر می‌دهد، اما سند داخل ظرف به صورت بصری مقیاس‌بندی می‌شود تا درون آن جا شود. عرض و ارتفاع گزارش‌شده سند جاسازی‌شده (یعنی {{domxref("Window.innerWidth")}} و {{domxref("Window.innerHeight")}}) بدون تغییر خواهند ماند.

## مقدار

یک رشته که عرض عنصر را بر حسب پیکسل‌های CSS نشان می‌دهد. مقدار پیش‌فرض `300` است.

## نمونه‌ها

```js
const frame = document.createElement("fencedframe");
frame.width = "480";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Fenced frames](https://privacysandbox.google.com/private-advertising/fenced-frame) در privacysandbox.google.com
- [The Privacy Sandbox](https://privacysandbox.google.com/) در privacysandbox.google.com
```