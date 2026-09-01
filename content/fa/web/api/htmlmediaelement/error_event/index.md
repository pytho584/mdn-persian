---
title: "HTMLMediaElement: error event"
short-title: error
slug: Web/API/HTMLMediaElement/error_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.error_event
---

{{APIRef("HTML DOM")}}

رویداد **`error`** زمانی رخ می‌دهد که منبع (resource) به دلیل یک خطا (مثلاً مشکل اتصال شبکه) بارگذاری نشود.

این رویداد قابل لغو (cancelable) نیست و bubble نمی‌کند.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک خاصیت کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("error", (event) => { })

onerror = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

```js
const video = document.querySelector("video");
const videoSrc = "https://path/to/video.webm";

video.addEventListener("error", () => {
  console.error(`Error loading: ${videoSrc}`);
});

video.setAttribute("src", videoSrc);
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLAudioElement")}}
- {{domxref("HTMLVideoElement")}}
- {{HTMLElement("audio")}}
- {{HTMLElement("video")}}