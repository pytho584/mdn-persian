---
title: "FontFaceSet: loading event"
short-title: loading
slug: Web/API/FontFaceSet/loading_event
page-type: web-api-event
browser-compat: api.FontFaceSet.loading_event
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

رویداد `loading` زمانی رخ می‌دهد که سند شروع به بارگذاری فونت‌ها می‌کند.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("loading", (event) => { })

onloading = (event) => { }
```

## Example

در مثال زیر، هنگامی که فونت `Ephesis` شروع به بارگذاری می‌کند، عبارت «Font is loading…» در کنسول چاپ می‌شود.

```js
document.fonts.onloading = () => {
  console.log("Font is loading");
};

(async () => {
  await document.fonts.load("16px Ephesis");
})();
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}