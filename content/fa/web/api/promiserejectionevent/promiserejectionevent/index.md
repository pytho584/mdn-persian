---
title: "PromiseRejectionEvent: PromiseRejectionEvent() constructor"
short-title: PromiseRejectionEvent()
slug: Web/API/PromiseRejectionEvent/PromiseRejectionEvent
page-type: web-api-constructor
browser-compat: api.PromiseRejectionEvent.PromiseRejectionEvent
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

سازنده‌ی **`PromiseRejectionEvent()`** یک شیء جدید {{domxref("PromiseRejectionEvent")}} برمی‌گرداند که رویدادهای مربوط به رد شدن (reject) یک {{jsxref("Promise")}} جاوااسکریپت را نشان می‌دهد.

با رویدادهای رد شدن وعده (Promise)، می‌توان وعده‌هایی را که ناموفق می‌شوند و خطای آن‌ها نادیده گرفته می‌شود شناسایی و گزارش کرد. همچنین نوشتن یک کنترل‌کننده‌ی سراسری برای خطاها آسان‌تر می‌شود.

دو نوع `PromiseRejectionEvent` وجود دارد: رویداد {{domxref("Window.unhandledrejection_event", "unhandledrejection")}} توسط زمان‌اجرای جاوااسکریپت وقتی ارسال می‌شود که یک وعده رد می‌شود اما این رد شدن بدون رسیدگی باقی می‌ماند. اگر وعده‌ای رد شود اما این رد شدن توسط یک هندلرِ رسیدگی به خطا گرفته شود، رویداد {{domxref("Window.rejectionhandled_event", "rejectionhandled")}} صادر می‌شود.

## نحو

```js-nolint
new PromiseRejectionEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای شامل نام رویداد. این مقدار به بزرگی/کوچکی حروف حساس است و مرورگرها آن را روی `rejectionhandled` یا `unhandledrejection` تنظیم می‌کنند.
- `options`
  - : شیءای که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_ می‌تواند ویژگی‌های زیر را داشته باشد:
    - `promise`
      - : {{jsxref("Promise")}}ای که رد شده است.
    - `reason`
      - : هر مقدار یا {{jsxref("Object")}}ای که دلیل رد شدن وعده را نشان می‌دهد. این می‌تواند هر چیزی باشد، از یک کد خطای عددی گرفته تا یک رشته‌ی خطا یا یک شیء حاوی اطلاعات دقیق درباره‌ی شرایطی که منجر به رد شدن وعده شده است.

### مقدار بازگشتی

یک شیء `PromiseRejectionEvent` جدید که مطابق پارامترهای داده‌شده پیکربندی شده است.

## مثال‌ها

این مثال یک رویداد جدید {{domxref("Window.unhandledrejection_event", "unhandledrejection")}} برای وعده‌ی `myPromise` با دلیلی به صورت رشته‌ی «My house is on fire» می‌سازد. `reason` می‌توانست به همین راحتی یک عدد یا حتی یک شیء با اطلاعات دقیق شامل آدرس خانه، میزان جدی بودن آتش‌سوزی و شماره تلفن یک فرد اضطراری که باید مطلع شود باشد.

```js
let myRejectionEvent = new PromiseRejectionEvent("unhandledrejection", {
  promise: myPromise,
  reason: "My house is on fire",
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از وعده‌ها](/en-US/docs/Web/JavaScript/Guide/Using_promises)
- {{jsxref("Promise")}}
- {{domxref("PromiseRejectionEvent")}}