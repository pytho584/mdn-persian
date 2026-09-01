---
title: "HTMLGeolocationElement: promptaction event"
short-title: promptaction
slug: Web/API/HTMLGeolocationElement/promptaction_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.HTMLGeolocationElement.promptaction_event
---

{{APIRef("HTML DOM")}}{{SeeCompatTable}}

رویداد **`promptaction`** از رابط {{domxref("HTMLGeolocationElement")}} هر زمان که کاربر عنصر `<geolocation>` را فعال کند و گزینه‌ای را از دیالوگ حاصل انتخاب کند، چه برای اعطای مجوز `geolocation` و چه برای رد آن، رخ می‌دهد.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("promptaction", (event) => { })

onpromptaction = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}}.

## مثال‌ها

### استفاده از `promptaction` برای پاسخ به انتخاب‌های مجوز کاربر

در [نمایش نقشه تعبیه‌شده](https://mdn.github.io/dom-examples/geolocation-element/embedded-map/) ما ([کد منبع](https://github.com/mdn/dom-examples/tree/main/geolocation-element/embedded-map))، از یک کنترل‌کننده رویداد `promptaction` برای پاسخ به انتخاب کاربر در اعلان مجوز `<geolocation>` استفاده می‌کنیم:

```js
geo.addEventListener("promptaction", notifyUserGrantPermission);
```

در تابع `notifyUserGrantPermission()`، از ویژگی {{domxref("HTMLGeolocationElement.permissionStatus")}} استفاده می‌کنیم تا بررسی کنیم که وضعیت مجوز `denied` (رد شده) یا `prompt` (درخواست) است و اگر چنین بود، از کاربر می‌خواهیم دوباره دکمه را فشار دهد و مکان را مجاز کند. اگر قبلاً مجوز داده‌اند، نیازی به این پرسش نداریم.

```js
function notifyUserGrantPermission() {
  if (geo.permissionStatus === "denied" || geo.permissionStatus === "prompt") {
    statusElem.textContent =
      'Please press the "Use location" button again and allow location for this site.';
  }
}
```

برای راهنمای کامل این مثال، صفحه اصلی {{domxref("HTMLGeolocationElement")}} را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{htmlelement("geolocation")}}