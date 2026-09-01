---
title: "FontFaceSet: loadingdone event"
short-title: loadingdone
slug: Web/API/FontFaceSet/loadingdone_event
page-type: web-api-event
browser-compat: api.FontFaceSet.loadingdone_event
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

رویداد `loadingdone` زمانی رخ می‌دهد که سند همهٔ فونت‌ها را بارگذاری کرده باشد.

## Syntax

می‌توانید نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا آن را به‌عنوان یک ویژگی مدیریت‌کنندهٔ رویداد تنظیم کنید.

```js-nolint
addEventListener("loadingdone", (event) => { })

onloadingdone = (event) => { }
```

## Example

در مثال زیر، وقتی بارگذاری فونت `Ephesis` به پایان برسد، پیام "Font loading complete" در کنسول چاپ می‌شود.

```js
document.fonts.onloadingdone = () => {
  console.log("Font loading complete");
};

(async () => {
  await document.fonts.load("16px Ephesis");
})();
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}