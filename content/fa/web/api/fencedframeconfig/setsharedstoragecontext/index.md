---
title: "FencedFrameConfig: setSharedStorageContext() method"
short-title: setSharedStorageContext()
slug: Web/API/FencedFrameConfig/setSharedStorageContext
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.FencedFrameConfig.setSharedStorageContext
---

{{APIRef("Fenced Frame API")}}{{SeeCompatTable}}

متد **`setSharedStorageContext()`** از رابط {{domxref("FencedFrameConfig")}} داده‌های زمینه‌ای را از سند جاساز به [shared storage](https://privacysandbox.google.com/private-advertising/shared-storage) درون `<fencedframe>` منتقل می‌کند.

## Syntax

```js-nolint
setSharedStorageContext(context)
```

### Parameters

- `context`
  - : یک رشته (string) که نشان‌دهنده داده‌های زمینه‌ای برای ارسال به shared storage است. پس از تنظیم، این داده در پیکربندی داخلی نمونه {{domxref("FencedFrameConfig")}} ذخیره می‌شود.

### Return value

هیچ‌کدام (`Undefined`).

## Examples

### ارسال داده‌های زمینه‌ای از طریق `setSharedStorageContext()`

شما می‌توانید از [Private Aggregation API](https://privacysandbox.google.com/private-advertising/private-aggregation) برای ایجاد گزارش‌هایی استفاده کنید که داده‌های سطح رویداد داخل fenced frames را با داده‌های زمینه‌ای از سند جاساز ترکیب می‌کنند. `setSharedStorageContext()` می‌تواند برای ارسال داده‌های زمینه‌ای از جاساز (embedder) به worklet‌های shared storage که توسط [Protected Audience API](https://privacysandbox.google.com/private-advertising/protected-audience) آغاز شده‌اند، استفاده شود.

در مثال زیر، داده‌هایی از هر دو صفحه جاساز و fenced frame در [shared storage](https://privacysandbox.google.com/private-advertising/shared-storage) ذخیره می‌کنیم.

در صفحه جاساز، یک شناسه رویداد ساختگی را به عنوان زمینه shared storage با استفاده از `setSharedStorageContext()` تنظیم می‌کنیم:

```js
const frameConfig = await navigator.runAdAuction({ resolveToConfig: true });

// Data from the embedder that you want to pass to the shared storage worklet
frameConfig.setSharedStorageContext("some-event-id");

const frame = document.createElement("fencedframe");
frame.config = frameConfig;
```

در داخل fenced frame، ماژول worklet را با {{domxref("Worklet.addModule","window.sharedStorage.worklet.addModule()")}} اضافه می‌کنیم و سپس داده‌های سطح رویداد را با استفاده از {{domxref("WindowSharedStorage.run","window.sharedStorage.run()")}} به worklet shared storage ارسال می‌کنیم (این کار ربطی به داده‌های زمینه‌ای از سند جاساز ندارد):

```js
const frameData = {
  // Data available only inside the fenced frame
};

await window.sharedStorage.worklet.addModule("reporting-worklet.js");

await window.sharedStorage.run("send-report", {
  data: {
    frameData,
  },
});
```

در worklet `reporting-worklet.js`، شناسه رویداد سند جاساز را از `sharedStorage.context` و داده‌های سطح رویداد فریم را از شیء داده می‌خوانیم و سپس آن‌ها را از طریق Private Aggregation گزارش می‌دهیم:

```js
class ReportingOperation {
  convertEventIdToBucket(eventId) {
    // …
  }
  convertEventPayloadToValue(info) {
    // …
  }

  async run(data) {
    // Data from the embedder
    const eventId = sharedStorage.context;

    // Data from the fenced frame
    const eventPayload = data.frameData;

    privateAggregation.sendHistogramReport({
      bucket: convertEventIdToBucket(eventId),
      value: convertEventPayloadToValue(eventPayload),
    });
  }
}

register("send-report", ReportingOperation);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Fenced frames](https://privacysandbox.google.com/private-advertising/fenced-frame) در privacysandbox.google.com
- [The Privacy Sandbox](https://privacysandbox.google.com/) در privacysandbox.google.com