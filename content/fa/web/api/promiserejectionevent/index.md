---
title: "PromiseRejectionEvent"
---

---
title: PromiseRejectionEvent
slug: Web/API/PromiseRejectionEvent
page-type: web-api-interface
browser-compat: api.PromiseRejectionEvent
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

رابطِ **`PromiseRejectionEvent`** رویدادهایی را نشان می‌دهد که وقتی یک {{jsxref("Promise")}} در جاوااسکریپت رد (reject) می‌شود، به بافتارِ سراسری اسکریپت ارسال می‌شوند. این رویدادها به‌ویژه برای تله‌متری و اشکال‌زدایی مفید هستند.

برای جزئیات بیشتر، به [رویدادهای رد شدن پرامیس](/en-US/docs/Web/JavaScript/Guide/Using_promises#promise_rejection_events) مراجعه کنید.

{{InheritanceDiagram}}

## سازنده

- {{domxref("PromiseRejectionEvent.PromiseRejectionEvent", "PromiseRejectionEvent()")}}
  - : با در نظر گرفتن نوع رویداد ([`unhandledrejection`](/en-US/docs/Web/API/Window/unhandledrejection_event) یا [`rejectionhandled`](/en-US/docs/Web/API/Window/rejectionhandled_event)) و سایر جزئیات، یک رویداد `PromiseRejectionEvent` می‌سازد.

## ویژگی‌های نمونه

_همچنین ویژگی‌ها را از والد خود، {{domxref("Event")}}، به ارث می‌برد._

- {{domxref("PromiseRejectionEvent.promise")}} {{ReadOnlyInline}}
  - : شیء {{jsxref("Promise")}} جاوااسکریپتی که رد شده است.
- {{domxref("PromiseRejectionEvent.reason")}} {{ReadOnlyInline}}
  - : یک مقدار یا {{jsxref("Object")}} که دلیل رد شدنِ پرامیس را نشان می‌دهد؛ همان مقداری که به {{jsxref("Promise.reject()")}} ارسال شده است.

## روش‌های نمونه

_این رابط هیچ روش منحصربه‌فردی ندارد و روش‌ها را از والد خود، {{domxref("Event")}}، به ارث می‌برد._

## رویدادها

- {{domxref("Window/rejectionhandled_event", "rejectionhandled")}}
  - : زمانی رخ می‌دهد که یک {{jsxref("Promise")}} در جاوااسکریپت رد شده باشد و سپس، این رد شدن توسط کدِ رسیدگی به رد شدنِ همان پرامیس مدیریت شود.
- {{domxref("Window/unhandledrejection_event", "unhandledrejection")}}
  - : زمانی رخ می‌دهد که یک {{jsxref("Promise")}} در جاوااسکریپت رد شده باشد، اما هیچ مدیریت‌کنندهٔ رد شدن (rejection handler) برای رسیدگی به آن وجود نداشته باشد.

## مثال‌ها

این مثال ساده، رویدادهای رد شدنِ مدیریت‌نشدهٔ پرامیس را دریافت می‌کند و برای اهداف اشکال‌زدایی در لاگ ثبت می‌کند.

```js
window.onunhandledrejection = (e) => {
  console.log(e.reason);
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از پرامیس‌ها](/en-US/docs/Web/JavaScript/Guide/Using_promises)
- {{jsxref("Promise")}}
- {{domxref("Window/rejectionhandled_event", "rejectionhandled")}}
- {{domxref("Window/unhandledrejection_event", "unhandledrejection")}}