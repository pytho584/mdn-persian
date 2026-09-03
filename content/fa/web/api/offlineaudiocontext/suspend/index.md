---
title: "OfflineAudioContext: suspend() method"
short-title: suspend()
slug: Web/API/OfflineAudioContext/suspend
page-type: web-api-instance-method
browser-compat: api.OfflineAudioContext.suspend
---

{{ APIRef("Web Audio API") }}

متد **`suspend()`** از رابط {{domxref("OfflineAudioContext")}} یک توقف موقت در پیشروی زمان در زمینه صوتی را در زمان مشخص شده زمان‌بندی کرده و یک promise بازمی‌گرداند. این معمولاً در زمان دستکاری همزمان گراف صوتی روی OfflineAudioContext مفید است.

توجه داشته باشید که حداکثر دقت توقف، اندازه کوانتوم رندر (render quantum) است و زمان توقف مشخص شده به نزدیک‌ترین مرز کوانتوم رندر گرد می‌شود. به همین دلیل، زمان‌بندی چندین توقف در همان فریم کوانتایز شده مجاز نیست. همچنین زمان‌بندی باید زمانی انجام شود که زمینه در حال اجرا نیست تا از توقف دقیق اطمینان حاصل شود.

## Syntax

```js-nolint
suspend(suspendTime)
```

### پارامترها

- `suspendTime`
  - : یک عدد اعشاری که زمان توقف را بر حسب ثانیه مشخص می‌کند.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به {{jsxref('undefined')}} resolution می‌یابد.

### استثناها

زمانی که هر استثنایی رخ دهد، promise رد می‌شود.

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر شماره فریم کوانتایز شده یکی از موارد زیر باشد بازگردانده می‌شود:
    - یک عدد منفی
    - کمتر یا مساوی با زمان فعلی
    - بزرگتر یا مساوی با کل مدت زمان رندر
    - توسط یک توقف دیگر برای همان زمان زمان‌بندی شده باشد

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
```