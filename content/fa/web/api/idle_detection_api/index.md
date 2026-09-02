---
title: Idle Detection API
slug: Web/API/Idle_Detection_API
page-type: web-api-overview
status:
  - experimental
browser-compat: api.IdleDetector
---

{{securecontext_header}}{{DefaultAPISidebar("Idle Detection API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_dedicated")}}

Idle Detection API امکانی را برای تشخیص وضعیت بیکار بودن کاربر فراهم می‌کند؛ به‌طور خاص وضعیت‌های «فعال» (active)، «بیکار» (idle) و «قفل‌شده» (locked) را شناسایی کرده و بدون نیاز به نظرسنجی (polling) از طریق اسکریپت، تغییرات وضعیت بیکاری را به اطلاع می‌رساند.

## مفاهیم و کاربرد

برنامه‌های بومی (Native) و افزونه‌های مرورگر، تشخیص بیکاری را مبنای تجربه‌های کاربری خود قرار می‌دهند تا مشخص کنند کاربر چه زمانی با دستگاه در تعامل است. به‌عنوان مثال، برنامه‌های گفتگو می‌توانند به سایر کاربران نشان دهند که آیا فردی در دسترس است یا خیر. برخی برنامه‌ها نیز ممکن است فقط زمانی اعلان‌ها را نشان دهند که کاربر با برنامه در تعامل است. یک برنامه وب می‌تواند برای موارد استفاده مشابه از این API بهره ببرد. علاوه بر این، یک برنامه وب پیشرونده (PWA) می‌تواند از تشخیص بیکاری برای فعال‌کردن به‌روزرسانی سرویس‌کارگر (Service Worker) زمانی که برنامه استفاده نمی‌شود، استفاده کند.

## رابط‌ها

- {{domxref("IdleDetector")}} {{Experimental_Inline}}
  - : روش‌ها و رویدادهایی را برای تشخیص فعالیت کاربر روی دستگاه یا صفحه‌نمایش فراهم می‌کند.

## نمونه‌ها

نمونه زیر نحوه ایجاد یک شناساگر (detector) و ثبت تغییرات وضعیت بیکاری کاربر را نشان می‌دهد. برای دریافت فعال‌سازی کاربر (user activation) لازم پیش از درخواست مجوز، از یک دکمه استفاده شده است.

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

## سازگاری مرورگرها

{{Compat}}