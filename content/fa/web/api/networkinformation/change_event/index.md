---
title: "NetworkInformation: change event"
short-title: change
slug: Web/API/NetworkInformation/change_event
page-type: web-api-event
browser-compat: api.NetworkInformation.change_event
---

{{apiref("Network Information API")}} {{AvailableInWorkers}}

رویداد **`change`** از رابط {{domxref("NetworkInformation")}} زمانی رخ می‌دهد که اطلاعات اتصال تغییر کند، و این رویداد توسط شیء {{domxref("NetworkInformation")}} دریافت می‌شود.

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("change", (event) => { })

onchange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

```js
// دریافت نوع اتصال.
const type = navigator.connection.type;

function changeHandler(e) {
  // تغییر نوع اتصال را اینجا مدیریت کنید.
}

// ثبت برای تغییرات رویداد:
navigator.connection.onchange = changeHandler;

// روش دیگر: navigator.connection.addEventListener('change', changeHandler);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}