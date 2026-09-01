---
title: "Element: fullscreenerror event"
short-title: fullscreenerror
slug: Web/API/Element/fullscreenerror_event
page-type: web-api-event
browser-compat: api.Element.fullscreenerror_event
---

{{APIRef("Fullscreen API")}}

رویداد **`fullscreenerror`** هنگامی که مرورگر نمی‌تواند به حالت تمام‌صفحه تغییر وضعیت دهد، فعال می‌شود.

مانند رویداد [`fullscreenchange`](/en-US/docs/Web/API/Element/fullscreenchange_event)، دو رویداد `fullscreenerror` فعال می‌شود؛ اولی به {{domxref("Element")}} که در تغییر وضعیت ناموفق بوده ارسال می‌شود، و دومی به {{domxref("Document")}} که مالک آن عنصر است.

برای برخی دلایل که ممکن است تغییر به حالت تمام‌صفحه با شکست مواجه شود، [راهنمای Fullscreen API](/en-US/docs/Web/API/Fullscreen_API/Guide) را ببینید.

این رویداد قابل لغو نیست.

## نحو

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم نمایید.

```js-nolint
addEventListener("fullscreenerror", (event) => { })

onfullscreenerror = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

```js
const requestor = document.querySelector("div");

function handleError(event) {
  console.error("an error occurred changing into fullscreen");
  console.log(event);
}

requestor.addEventListener("fullscreenerror", handleError);
// or
requestor.onfullscreenerror = handleError;

requestor.requestFullscreen();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [`fullscreenchange`](/en-US/docs/Web/API/Element/fullscreenchange_event)
- [Fullscreen API](/en-US/docs/Web/API/Fullscreen_API)
- [راهنمای Fullscreen API](/en-US/docs/Web/API/Fullscreen_API/Guide)