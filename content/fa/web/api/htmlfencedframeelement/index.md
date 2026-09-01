---
title: "HTMLFencedFrameElement"
slug: Web/API/HTMLFencedFrameElement
page-type: web-api-interface
status:
  - experimental
browser-compat: api.HTMLFencedFrameElement
---

{{SeeCompatTable}}{{APIRef("Fenced Frame API")}}

رابطِ **`HTMLFencedFrameElement`** عنصرِ {{htmlelement("fencedframe")}} را در جاوااسکریپت نمایش می‌دهد و ویژگی‌های پیکربندی آن را فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("HTMLElement")}} به ارث می‌برد._

- {{domxref("HTMLFencedFrameElement.allow")}} {{experimental_inline}}
  - : مقدارِ ویژگی `allow` مربوط به `<fencedframe>` را دریافت و تنظیم می‌کند. این ویژگی نمایانگر یک [سیاست مجوزها](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) است که هنگام اولین جاسازی بر محتوا اعمال می‌شود.
- {{domxref("HTMLFencedFrameElement.config")}} {{experimental_inline}}
  - : یک شیء {{domxref("FencedFrameConfig")}} که ناوبری یک {{htmlelement("fencedframe")}} را نشان می‌دهد؛ یعنی اینکه چه محتوایی در آن نمایش داده خواهد شد. یک `FencedFrameConfig` از منبعی مانند [Protected Audience API](https://privacysandbox.google.com/private-advertising/protected-audience) بازگردانده می‌شود.
- {{domxref("HTMLFencedFrameElement.height")}} {{experimental_inline}}
  - : مقدارِ ویژگی `height` مربوط به `<fencedframe>` را دریافت و تنظیم می‌کند که ارتفاع عنصر را مشخص می‌کند.
- {{domxref("HTMLFencedFrameElement.width")}} {{experimental_inline}}
  - : مقدارِ ویژگی `width` مربوط به `<fencedframe>` را دریافت و تنظیم می‌کند که عرض عنصر را مشخص می‌کند.

## مثال‌ها

برای تنظیم محتوایی که در یک `<fencedframe>` نمایش داده می‌شود، یک API استفاده‌کننده (مانند [Protected Audience](https://privacysandbox.google.com/private-advertising/protected-audience) یا [Shared Storage](https://privacysandbox.google.com/private-advertising/shared-storage)) یک شیء {{domxref("FencedFrameConfig")}} تولید می‌کند که سپس به عنوان مقدارِ ویژگی `config` عنصر `<fencedframe>` تنظیم می‌شود.

مثال زیر یک `FencedFrameConfig` را از یک حراجی آگهی در Protected Audience API دریافت می‌کند و سپس از آن برای نمایش آگهی برنده در یک `<fencedframe>` استفاده می‌شود:

```js
const frameConfig = await navigator.runAdAuction({
  // … پیکربندی حراجی
  resolveToConfig: true,
});

const frame = document.createElement("fencedframe");
frame.config = frameConfig;
```

> [!NOTE]
> برای دریافت شیء `FencedFrameConfig`، باید `resolveToConfig: true` را در فراخوانی `runAdAuction()` ارسال کنید. اگر تنظیم نشود، {{jsxref("Promise")}} حاصل به یک URN حل می‌شود که فقط می‌تواند در یک {{htmlelement("iframe")}} استفاده شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Fenced frames](https://privacysandbox.google.com/private-advertising/fenced-frame) در privacysandbox.google.com
- [The Privacy Sandbox](https://privacysandbox.google.com/) در privacysandbox.google.com