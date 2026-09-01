---
title: "Document: fullscreenerror event"
short-title: fullscreenerror
slug: Web/API/Document/fullscreenerror_event
page-type: web-api-event
browser-compat: api.Document.fullscreenerror_event
---

{{APIRef("Fullscreen API")}}

رویداد **`fullscreenerror`** زمانی به وجود می‌آید که مرورگر نتواند به حالت تمام‌صفحه (fullscreen) برود.

همانند رویداد [`fullscreenchange`](/en-US/docs/Web/API/Document/fullscreenchange_event)، دو رویداد `fullscreenerror` ارسال می‌شود؛ اولی به {{domxref("Element")}} که نتوانسته وضعیت خود را تغییر دهد ارسال می‌شود و دومی به {{domxref("Document")}} که مالک آن عنصر است.

برای آگاهی از برخی دلایلی که ممکن است باعث شکست تغییر به حالت تمام‌صفحه شوند، به [راهنمای Fullscreen API](/en-US/docs/Web/API/Fullscreen_API/Guide) مراجعه کنید.

این رویداد قابل ابطال (cancelable) نیست.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید یا یک ویژگی handler رویداد تنظیم کنید.

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

document.addEventListener("fullscreenerror", handleError);
// or
document.onfullscreenerror = handleError;

requestor.requestFullscreen();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document/fullscreenchange_event", "fullscreenchange")}}
- {{domxref("Element")}}: رویداد {{domxref("Element/fullscreenerror_event", "fullscreenerror")}}
- [Fullscreen API](/en-US/docs/Web/API/Fullscreen_API)
- [راهنمای Fullscreen API](/en-US/docs/Web/API/Fullscreen_API/Guide)