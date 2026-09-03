---
title: "PromiseRejectionEvent: promise property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/PromiseRejectionEvent/promise"
---

---
title: "PromiseRejectionEvent: promise property"
short-title: promise
slug: Web/API/PromiseRejectionEvent/promise
page-type: web-api-instance-property
browser-compat: api.PromiseRejectionEvent.promise
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`promise`** در رابط {{domxref("PromiseRejectionEvent")}}، نشانی از {{jsxref("Promise")}} جاوااسکریپتی است که رد شده است. می‌توانید با بررسی ویژگی {{domxref("PromiseRejectionEvent.reason")}} رویداد، دلیل رد شدن promise را بیابید.

## مقدار

{{jsxref("Promise")}} جاوااسکریپتی که رد شده و رد شدن آن بدون رسیدگی باقی مانده است.

## نمونه‌ها

این مثال به رویدادهای promise‌های بدون رسیدگی گوش می‌دهد و اگر {{domxref("PromiseRejectionEvent.reason", "reason")}} یک شیء با فیلد `code` به متن «Module not ready» باشد، یک callback بیکار (idle callback) تنظیم می‌کند که وظیفه‌ی شکست‌خورده را دوباره تلاش کند.

{{domxref("event.preventDefault()")}} فراخوانی می‌شود تا نشان دهد که اکنون به این promise رسیدگی شده است.

```js
window.onunhandledrejection = (event) => {
  if (event.reason?.code === "Module not ready") {
    requestIdleCallback((deadline) => {
      loadModule(event.reason.moduleName).then(performStartup);
    });
    event.preventDefault();
  }
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رویدادهای رد شدن promise](/en-US/docs/Web/JavaScript/Guide/Using_promises#promise_rejection_events)
- {{jsxref("Promise")}}
- {{domxref("PromiseRejectionEvent")}}
- {{domxref("Window.rejectionhandled_event", "rejectionhandled")}}
- {{domxref("Window.unhandledrejection_event", "unhandledrejection")}}