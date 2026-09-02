---
title: "IdleDetector"
slug: Web/API/IdleDetector
page-type: web-api-interface
status:
  - experimental
browser-compat: api.IdleDetector
---

{{securecontext_header}}{{APIRef("Idle Detection API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_dedicated")}}

رابط **`IdleDetector`** از {{domxref('idle_detection_api','Idle Detection API','','true')}} روش‌ها و رویدادهایی برای تشخیص فعالیت کاربر روی دستگاه یا صفحه ارائه می‌دهد.

این رابط به یک متن امن (secure context) نیاز دارد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("IdleDetector.IdleDetector", "IdleDetector()")}} {{Experimental_Inline}}
  - : یک شیء جدید `IdleDetector` می‌سازد.

## ویژگی‌های نمونه

- {{domxref("IdleDetector.userState")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک رشته برمی‌گرداند که نشان می‌دهد آیا کاربر در بازه زمانی تعیین‌شده برای `start()` با صفحه یا دستگاه تعامل داشته است یا خیر؛ یکی از `"active"` یا `"idle"`. این ویژگی قبل از فراخوانی `start()` مقدار `null` برمی‌گرداند.
- {{domxref("IdleDetector.screenState")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک رشته برمی‌گرداند که نشان می‌دهد صفحه قفل است یا خیر؛ یکی از `"locked"` یا `"unlocked"`. این ویژگی قبل از فراخوانی `start()` مقدار `null` برمی‌گرداند.

## رویدادها

- {{domxref("IdleDetector.change_event", "change")}} {{Experimental_Inline}}
  - : زمانی که مقدار `userState` یا `screenState` تغییر کند، فراخوانی می‌شود.

## روش‌های ایستا

- {{domxref("IdleDetector/requestPermission_static", "IdleDetector.requestPermission()")}} {{Experimental_Inline}}
  - : یک {{jsxref('Promise')}} برمی‌گرداند که وقتی کاربر تصمیم خود را برای اعطای دسترسی به مبدأ (origin) برای وضعیت بیکاری‌اش اعلام کرد، حل می‌شود. در صورت پذیرش با `"granted"` و در صورت رد با `"denied"` حل می‌شود.

## روش‌های نمونه

- {{domxref("IdleDetector.start()")}} {{Experimental_Inline}}
  - : یک `Promise` برمی‌گرداند که وقتی تشخیص‌دهنده شروع به شنیدن تغییرات وضعیت بیکاری کاربر کند، حل می‌شود. `userState` و `screenState` مقادیر اولیه می‌گیرند. این روش یک شیء اختیاری `options` با `threshold` (آستانه) بر حسب میلی‌ثانیه که در آن بیکاری گزارش شود، و `signal` برای یک `AbortSignal` برای لغو تشخیص‌دهنده بیکاری می‌پذیرد.

## مثال‌ها

مثال زیر یک تشخیص‌دهنده ایجاد کرده و تغییرات وضعیت بیکاری کاربر را ثبت می‌کند. از یک دکمه برای دریافت فعال‌سازی کاربر لازم قبل از درخواست مجوز استفاده شده است.

```js
const controller = new AbortController();
const signal = controller.signal;

startButton.addEventListener("click", async () => {
  if ((await IdleDetector.requestPermission()) !== "granted") {
    console.error("Idle detection permission denied.");
    return;
  }

  try {
    const idleDetector = new IdleDetector();
    idleDetector.addEventListener("change", () => {
      const userState = idleDetector.userState;
      const screenState = idleDetector.screenState;
      console.log(`Idle change: ${userState}, ${screenState}.`);
    });

    await idleDetector.start({
      threshold: 60_000,
      signal,
    });
    console.log("IdleDetector is active.");
  } catch (err) {
    // Deal with initialization errors like permission denied,
    // running outside of top-level frame, etc.
    console.error(err.name, err.message);
  }
});

stopButton.addEventListener("click", () => {
  controller.abort();
  console.log("IdleDetector is stopped.");
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}