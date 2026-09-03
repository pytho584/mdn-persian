---
title: "PromiseRejectionEvent: reason property"
short-title: reason
slug: Web/API/PromiseRejectionEvent/reason
page-type: web-api-instance-property
browser-compat: api.PromiseRejectionEvent.reason
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

خاصیت فقط‌خواندنی **`reason`** در {{domxref("PromiseRejectionEvent")}}، هر مقدار یا {{jsxref("Object")}} در جاوااسکریپت است که دلیلی را که به {{jsxref("Promise.reject()")}} منتقل شده، فراهم می‌کند. این مقدار در تئوری اطلاعاتی دربارهٔ دلیل رد شدن پرامیس در اختیار شما قرار می‌دهد.

## مقدار

مقدار یا شیءای که اطلاعاتی برای درک دلیل رد شدن پرامیس فراهم می‌کند. این می‌تواند هر چیزی باشد، از یک کد خطا تا شیءای شامل متن، پیوندها و هر آنچه که بخواهید در آن بگنجانید.

## مثال‌ها

```js
window.onunhandledrejection = (e) => {
  console.log(e.reason);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{jsxref("Promise")}}
- {{domxref("PromiseRejectionEvent")}}
- {{domxref("Window.rejectionhandled_event", "rejectionhandled")}}
- {{domxref("Window.unhandledrejection_event", "unhandledrejection")}}