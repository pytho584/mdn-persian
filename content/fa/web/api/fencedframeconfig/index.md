---
title: FencedFrameConfig
slug: Web/API/FencedFrameConfig
page-type: web-api-interface
status:
  - experimental
browser-compat: api.FencedFrameConfig
---

{{SeeCompatTable}}{{APIRef("Fenced Frame API")}}

رابط **`FencedFrameConfig`** نمایانگر مسیریابی یک {{htmlelement("fencedframe")}} است، یعنی محتوایی که در آن نمایش داده خواهد شد.

اشیاء `FencedFrameConfig` را نمی‌توان به صورت دستی از طریق جاوااسکریپت ایجاد کرد. آن‌ها از یک منبع مانند [Protected Audience API](https://privacysandbox.google.com/private-advertising/protected-audience) بازگردانده می‌شوند و به عنوان مقدار {{domxref("HTMLFencedFrameElement.config")}} تنظیم می‌شوند.

یک نمونه از شیء `FencedFrameConfig` دارای یک متد آشکار است، اما همچنین به اطلاعات پیکربندی داخلی نگاشت می‌شود که شامل ویژگی‌های مبهمی است که از جاوااسکریپت قابل دسترسی نیستند. این شامل اطلاعاتی مانند منبع محتوای بارگذاری‌شده و گروه‌های علاقه‌مندی برای اهداف تبلیغاتی است. این امر کلید نحوه کمک فریم‌های حصاردار به پیاده‌سازی موارد استفاده کلیدی در عین رعایت حریم خصوصی کاربر است.

{{InheritanceDiagram}}

## روش‌های نمونه

- {{domxref("FencedFrameConfig.setSharedStorageContext", "setSharedStorageContext()")}} {{experimental_inline}}
  - : داده‌ها را از سند جاساز به ذخیره‌سازی اشتراکی `<fencedframe>` منتقل می‌کند.

## مثال‌ها

### استفاده پایه

برای تنظیم محتوایی که در یک `<fencedframe>` نمایش داده می‌شود، یک API استفاده‌کننده (مانند [Protected Audience](https://privacysandbox.google.com/private-advertising/protected-audience) یا [Shared Storage](https://privacysandbox.google.com/private-advertising/shared-storage)) یک شیء `FencedFrameConfig` ایجاد می‌کند که سپس به عنوان مقدار ویژگی `config` عنصر `<fencedframe>` تنظیم می‌شود.

مثال زیر یک `FencedFrameConfig` را از یک حراج تبلیغاتی API Protected Audience دریافت می‌کند که سپس برای نمایش تبلیغ برنده در یک `<fencedframe>` استفاده می‌شود:

```js
const frameConfig = await navigator.runAdAuction({
  // … پیکربندی حراج
  resolveToConfig: true,
});

const frame = document.createElement("fencedframe");
frame.config = frameConfig;
```

> [!NOTE]
> برای به دست آوردن یک شیء `FencedFrameConfig`، باید `resolveToConfig: true` به فراخوانی `runAdAuction()` ارسال شود. اگر تنظیم نشود، {{jsxref("Promise")}} حاصل به یک URN حل می‌شود که فقط در یک {{htmlelement("iframe")}} قابل استفاده است.

### ارسال داده‌های زمینه‌ای از طریق `setSharedStorageContext()`

می‌توانید از [Private Aggregation API](https://privacysandbox.google.com/private-advertising/private-aggregation) برای ایجاد گزارش‌هایی استفاده کنید که داده‌های سطح رویداد درون فریم‌های حصاردار را با داده‌های زمینه‌ای از سند جاساز ترکیب می‌کنند. `setSharedStorageContext()` می‌تواند برای ارسال داده‌های زمینه‌ای از جاساز به worklet‌های ذخیره‌سازی اشتراکی که توسط [Protected Audience API](https://privacysandbox.google.com/private-advertising/protected-audience) آغاز شده‌اند، استفاده شود.

در مثال زیر، داده‌هایی را از هر دو صفحه جاساز و فریم حصاردار در [ذخیره‌سازی اشتراکی](https://privacysandbox.google.com/private-advertising/shared-storage) ذخیره می‌کنیم.

در صفحه جاساز، یک شناسه رویداد ساختگی را با استفاده از `setSharedStorageContext()` به عنوان زمینه ذخیره‌سازی اشتراکی تنظیم می‌کنیم:

```js
const frameConfig = await navigator.runAdAuction({ resolveToConfig: true });

// داده‌ای از جاساز که می‌خواهید به worklet ذخیره‌سازی اشتراکی ارسال کنید
frameConfig.setSharedStorageContext("some-event-id");

const frame = document.createElement("fencedframe");
frame.config = frameConfig;
```

درون فریم حصاردار، ماژول worklet را با {{domxref("Worklet.addModule","window.sharedStorage.worklet.addModule()")}} اضافه می‌کنیم و سپس داده‌های سطح رویداد را با استفاده از {{domxref("WindowSharedStorage.run","window.sharedStorage.run()")}} به worklet ذخیره‌سازی اشتراکی ارسال می‌کنیم (این به داده‌های زمینه‌ای از سند جاساز ارتباطی ندارد):

```js
const frameData = {
  // داده‌ای که فقط درون فریم حصاردار در دسترس است
};

await window.sharedStorage.worklet.addModule("reporting-worklet.js");

await window.sharedStorage.run("send-report", {
  data: {
    frameData,
  },
});
```

در worklet `reporting-worklet.js`، شناسه رویداد سند جاساز را از `sharedStorage.context` و داده‌های سطح رویداد فریم را از شیء داده می‌خوانیم و سپس آن‌ها را از طریق [Private Aggregation](https://privacysandbox.google.com/private-advertising/private-aggregation) گزارش می‌دهیم:

```js
class ReportingOperation {
  convertEventIdToBucket(eventId) {
    // …
  }
  convertEventPayloadToValue(info) {
    // …
  }

  async run(data) {
    // داده از جاساز
    const eventId = sharedStorage.context;

    // داده از فریم حصاردار
    const eventPayload = data.frameData;

    privateAggregation.sendHistogramReport({
      bucket: convertEventIdToBucket(eventId),
      value: convertEventPayloadToValue(eventPayload),
    });
  }
}

register("send-report", ReportingOperation);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [فریم‌های حصاردار (Fenced frames)](https://privacysandbox.google.com/private-advertising/fenced-frame) در privacysandbox.google.com
- [Privacy Sandbox](https://privacysandbox.google.com/) در privacysandbox.google.com