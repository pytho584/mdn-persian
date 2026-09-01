---
title: "FontFaceSet: loadingerror event"
short-title: loadingerror
slug: Web/API/FontFaceSet/loadingerror_event
page-type: web-api-event
browser-compat: api.FontFaceSet.loadingerror_event
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

رویداد `loadingerror` زمانی رخ می‌دهد که بارگذاری فونت‌ها به پایان رسیده باشد، اما برخی یا همهٔ فونت‌ها با شکست مواجه شده‌اند.

## نحو (Syntax)

برای استفاده از نام این رویداد می‌توانید از روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی (property) برای مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("loadingerror", (event) => { })

onloadingerror = (event) => { }
```

## مثال

در مثال زیر، اگر فونت `Ephesis` بارگذاری نشود، عبارت «خطای بارگذاری فونت» در کنسول چاپ می‌شود.

```js
document.fonts.onloadingerror = () => {
  console.log("Font loading error");
};

(async () => {
  await document.fonts.load("16px Ephesis");
})();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}