---
title: "IdleDetector: change event"
short-title: change
slug: Web/API/IdleDetector/change_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.IdleDetector.change_event
---

{{securecontext_header}}{{APIRef("Idle Detection API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_dedicated")}}

رویداد **`change`** در واسط {{domxref("IdleDetector")}} زمانی رخ می‌دهد که مقدار `userState` یا `screenState` تغییر کرده باشد.

## نحو و دستور

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("change", (event) => { })

onchange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال

در مثال زیر، فراخوان رویداد `change` وضعیت `userState` و `screenState` را در کنسول چاپ می‌کند.

```js
idleDetector.addEventListener("change", () => {
  const userState = idleDetector.userState;
  const screenState = idleDetector.screenState;
  console.log(`Idle change: ${userState}, ${screenState}.`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}