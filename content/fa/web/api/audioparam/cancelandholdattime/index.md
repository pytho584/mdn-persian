---
title: "AudioParam: cancelAndHoldAtTime() method"
short-title: cancelAndHoldAtTime()
slug: Web/API/AudioParam/cancelAndHoldAtTime
page-type: web-api-instance-method
browser-compat: api.AudioParam.cancelAndHoldAtTime
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioParam/cancelAndHoldAtTime"
translated_by: "n8n + AI"
---

{{APIRef("Web Audio API")}}

**`cancelAndHoldAtTime()`** از رابط {{domxref("AudioParam")}} تمام تغییرات زمان‌بندی شده آینده در `AudioParam` را لغو می‌کند اما مقدار آن را در یک زمان مشخص حفظ می‌کند تا زمانی که تغییرات دیگری با استفاده از روش‌های دیگر اعمال شود.

## نحو

```js-nolint
cancelAndHoldAtTime(cancelTime)
```

### پارامترها

- `cancelTime`
  - : یک عدد اعشاری که نشان‌دهنده زمان (به ثانیه) پس از ایجاد اولیه [`AudioContext`](/en-US/docs/Web/API/AudioContext) است که پس از آن تمام تغییرات زمان‌بندی شده لغو خواهند شد.

### مقدار بازگشتی

یک ارجاع به {{domxref("AudioParam")}} که این روش روی آن فراخوانی شده است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}