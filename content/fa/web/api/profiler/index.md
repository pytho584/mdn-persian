---
title: Profiler
slug: Web/API/Profiler
page-type: web-api-interface
status:
  - experimental
browser-compat: api.Profiler
---

{{APIRef("JS Self-Profiling API")}}{{SeeCompatTable}}

رابط **`Profiler`** در [JS Self-Profiling API](/en-US/docs/Web/API/JS_Self-Profiling_API) به شما این امکان را می‌دهد که از بخشی از اجرای برنامهٔ وب خود یک [پروفایل](/en-US/docs/Web/API/JS_Self-Profiling_API/Profile_content_and_format) ایجاد کنید.

## سازنده

- {{domxref("Profiler.Profiler","Profiler()")}} {{experimental_inline}}
  - : یک شیء `Profiler` جدید می‌سازد و شروع به جمع‌آوری نمونه‌ها می‌کند.

## متدهای نمونه

- {{domxref("Profiler.stop()")}} {{experimental_inline}}
  - : پروفایلر را متوقف می‌کند و یک {{jsxref("Promise")}} برمی‌گرداند که به [پروفایل](/en-US/docs/Web/API/JS_Self-Profiling_API/Profile_content_and_format) resolve می‌شود.

## رویدادها

- {{domxref("Profiler.samplebufferfull_event", "samplebufferfull")}}
  - : هنگامی رخ می‌دهد که پروفایل به اندازهٔ کافی نمونه ضبط کرده باشد تا بافر داخلی آن پر شود.

## مثال‌ها

### ثبت یک پروفایل

کد زیر عملیات `doWork()` را پروفایل می‌کند و نتیجه را در کنسول لاگ می‌کند.

```js
const profiler = new Profiler({ sampleInterval: 10, maxBufferSize: 10000 });

doWork();

const profile = await profiler.stop();
console.log(JSON.stringify(profile));
```

### پروفایل‌گیری از بارگذاری صفحه

کد زیر مدت زمان بین اجرای اولیهٔ اسکریپت و رخ دادن رویداد {{domxref("Window.load_event", "load")}} پنجره را پروفایل می‌کند.

```js
const profiler = new Profiler({ sampleInterval: 10, maxBufferSize: 10000 });

window.addEventListener("load", async () => {
  const profile = await profiler.stop();
  console.log(JSON.stringify(profile));
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}