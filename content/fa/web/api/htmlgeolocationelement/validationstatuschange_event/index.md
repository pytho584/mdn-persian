---
title: "HTMLGeolocationElement: validationstatuschange event"
short-title: validationstatuschange
slug: Web/API/HTMLGeolocationElement/validationstatuschange_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.HTMLGeolocationElement.validationstatuschange_event
---

{{APIRef("HTML DOM")}}{{SeeCompatTable}}

رویداد **`validationstatuschange`** از رابط {{domxref("HTMLGeolocationElement")}} هر زمان که مقدار {{domxref("HTMLGeolocationElement.isValid", "isValid")}} عنصر {{htmlelement("geolocation")}} تغییر کند صادر می‌شود.

این اتفاق در نتیجهٔ افزودن یا حذف یک [مسدودکننده](/en-US/docs/Web/HTML/Reference/Elements/geolocation#geolocation_blocking) به/از یک عنصر `<geolocation>` رخ می‌دهد.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کنندهٔ رویداد تنظیم کنید.

```js-nolint
addEventListener("validationstatuschange", (event) => { })

onvalidationstatuschange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}}.

## مثال‌ها

### استفاده از `validationstatuschange` برای گزارش دلایل نامعتبر

در [نمایش زندهٔ بررسی دلایل نامعتبر](https://mdn.github.io/dom-examples/geolocation-element/exploring-invalid-reasons/) ([کد منبع](https://github.com/mdn/dom-examples/tree/main/geolocation-element/exploring-invalid-reasons))، از یک کنترل‌کنندهٔ رویداد `validationstatuschange` استفاده می‌کنیم تا زمان معتبر شدن یک عنصر `<geolocation>` را گزارش دهیم و وقتی نامعتبر می‌شود، دلیل نامعتبر بودن را گزارش کنیم:

```js
geo.addEventListener("validationstatuschange", () => {
  if (geo.isValid) {
    reasonElem.textContent = `<geolocation> is valid`;
  } else {
    reasonElem.textContent = `Invalid reason: ${geo.invalidReason}`;
  }
});
```

هر بار که وضعیت اعتبارسنجی تغییر می‌کند، با استفاده از {{domxref("HTMLGeolocationElement.isValid")}} بررسی می‌کنیم که آیا عنصر `<geolocation>` معتبر است یا نه. اگر معتبر بود، پیامی تأییدکننده در محتوای متنی عنصر `<p>` می‌نویسیم. اگر عنصر `<geolocation>` نامعتبر باشد، مقدار {{domxref("HTMLGeolocationElement.invalidReason")}} را در محتوای متنی عنصر `<p>` می‌نویسیم.

برای شرح کامل این مثال، صفحهٔ {{domxref("HTMLGeolocationElement.invalidReason")}} را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{htmlelement("geolocation")}}
