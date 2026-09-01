---
title: "HTMLGeolocationElement: promptdismiss event"
short-title: promptdismiss
slug: Web/API/HTMLGeolocationElement/promptdismiss_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.HTMLGeolocationElement.promptdismiss_event
---

{{APIRef("HTML DOM")}}{{SeeCompatTable}}

رویداد **`promptdismiss`** از رابط {{domxref("HTMLGeolocationElement")}} زمانی فعال می‌شود که کاربر عنصر `<geolocation>` را فعال کند و گفت‌وگوی حاصل را با فشار دادن دکمه «بستن» یا کلید <kbd>Esc</kbd> رد کند.

## نحو (Syntax)

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا تنظیم ویژگی handler رویداد می‌توانید به شکل زیر عمل کنید:

```js-nolint
addEventListener("promptdismiss", (event) => { })

onpromptdismiss = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}}.

## مثال‌ها

### استفاده از `promptdismiss` برای پاسخ به رد کردن مجوز توسط کاربر

در [دموی نقشه جاسازی‌شده](https://mdn.github.io/dom-examples/geolocation-element/embedded-map/) ما ([کد منبع](https://github.com/mdn/dom-examples/tree/main/geolocation-element/embedded-map))، از handler رویداد `promptdismiss` برای پاسخ به رد کردن اعلان مجوز `<geolocation>` توسط کاربر استفاده کرده‌ایم:

```js
geo.addEventListener("promptdismiss", notifyUserRetrySelection);
```

در تابع `notifyUserRetrySelection()`، از کاربر می‌خواهیم دوباره دکمه را فشار دهد و موقعیت مکانی را مجاز کند.

```js
function notifyUserRetrySelection() {
  statusElem.textContent =
    'Please press the "Use location" button again and allow location for this site.';
}
```

برای توضیح کامل این مثال، صفحه اصلی {{domxref("HTMLGeolocationElement")}} را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{htmlelement("geolocation")}}