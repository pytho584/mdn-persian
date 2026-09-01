---
title: "Fence: reportEvent() method"
short-title: reportEvent()
slug: Web/API/Fence/reportEvent
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Fence.reportEvent
---

{{SeeCompatTable}}{{APIRef("Fenced Frame API")}}

متد **`reportEvent()`** از رابط {{domxref("Fence")}} باعث ارسال داده‌های گزارش از طریق یک [beacon](/en-US/docs/Web/API/Beacon_API) به یک یا چند URL مشخص می‌شود که از طریق متد {{domxref("InterestGroupReportingScriptRunnerGlobalScope.registerAdBeacon", "registerAdBeacon()")}} از [Protected Audience API](https://privacysandbox.google.com/private-advertising/protected-audience) ثبت شده‌اند، به منظور جمع‌آوری نتایج حراج تبلیغات.

> [!NOTE]
> {{domxref("Fence.setReportEventDataForAutomaticBeacons", "setReportEventDataForAutomaticBeacons()")}} ارسال داده‌های گزارش مشابهی را ارائه می‌دهد، با این تفاوت که در آن حالت ارسال به جای فراخوانی صریح متد، از طریق یک پیمایش (navigation) انجام می‌شود.

## Syntax

```js-nolint
reportEvent(event)
```

### Parameters

- `event`
  - : یک شیء یا رشته که داده‌های ارسالی را مشخص می‌کند.
    - یک مقدار شیء، یک رویداد گزارش خاص را تعریف می‌کند که می‌خواهید ارسال کنید. ویژگی‌های مورد نیاز به شرح زیر است:
      - `eventType`
        - : رشته‌ای که نوع رویداد گزارش‌شده را مشخص می‌کند – برای مثال ممکن است به تعداد دفعات کلیک روی یک آگهی علاقه‌مند باشید. این رشته می‌تواند هر نام رویداد مرتبطی باشد (مانند [`click`](/en-US/docs/Web/API/Element/click_event)). این مقدار باید با نوع رویداد مشخص‌شده در فراخوانی {{domxref("InterestGroupReportingScriptRunnerGlobalScope.registerAdBeacon", "registerAdBeacon()")}} در یک worklet از [Protected Audience API](https://privacysandbox.google.com/private-advertising/protected-audience) مطابقت داشته باشد.
      - `eventData`
        - : رشته‌ای که داده‌های ارسالی را نشان می‌دهد.
      - `destination`
        - : آرایه‌ای شامل یک یا چند مقدار شمارشی که انواع مقصد را مشخص می‌کند. این‌ها طرف‌های درگیر هستند که داده‌ها را به URLهای ثبت‌شده خود (یعنی از طریق {{domxref("InterestGroupReportingScriptRunnerGlobalScope.registerAdBeacon", "registerAdBeacon()")}}) دریافت می‌کنند. مقادیر ممکن عبارتند از:
          - `"buyer"`: پیشنهاددهنده در حراج تبلیغات.
          - `"seller"`: فروشنده سطح بالا که حراج تبلیغات را اجرا می‌کند.
          - `"component-seller"`: فروشنده یک حراج جزء در یک حراج چندسطحی.
          - `"direct-seller"`: فروشنده‌ای که مستقیماً حراجی را که خریدار در آن پیشنهاد داده اجرا کرده است. اگر آگهی مربوط به یک حراج تک‌سطحی باشد، مقدار استفاده‌شده `"seller"` خواهد بود. اگر آگهی مربوط به یک حراج چندسطحی باشد، مقدار استفاده‌شده `"component-seller"` خواهد بود.
          - `"shared-storage-select-url"`: یک مکان ذخیره‌سازی از [Shared Storage API](https://privacysandbox.google.com/private-advertising/shared-storage) که در فراخوانی متد {{domxref("WindowSharedStorage.selectURL", "Window.sharedStorage.selectURL()")}} تعریف شده است.
    - یک مقدار رشته‌ای یک `eventType` را نشان می‌دهد، برای مثال `"click"` (به تعریف قبلی `eventType` مراجعه کنید). هنگامی که یک رشته `eventType` به عنوان مقدار `reportEvent()` ارسال می‌شود، تمام مشارکت‌های Private Aggregation که به آن نوع رویداد وابسته شده‌اند (مثلاً از طریق {{domxref("PrivateAggregation.contributeToHistogramOnEvent()")}}) را برای ارسال فعال می‌کند.

### Return value

هیچ‌کدام (`Undefined`).

## Examples

```js
window.fence.reportEvent({
  eventType: "click",
  eventData: JSON.stringify({ clickX: "123", clickY: "456" }),
  destination: ["buyer", "seller"],
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Fenced frames](https://privacysandbox.google.com/private-advertising/fenced-frame) on privacysandbox.google.com
- [The Privacy Sandbox](https://privacysandbox.google.com/) on privacysandbox.google.com