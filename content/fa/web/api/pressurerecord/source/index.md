---
title: "PressureRecord: source property"
short-title: source
slug: Web/API/PressureRecord/source
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PressureRecord.source
---

{{APIRef("Compute Pressure API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_service")}}{{securecontext_header}}

ویژگی فقط‌خواندنی **`source`** یک رشته است که نشان می‌دهد رکورد از کدام منبع می‌آید.

## مقدار

یک رشته که نشان می‌دهد رکورد از کدام منبع می‌آید. نسخهٔ فعلی مشخصات Compute Pressure API دو نوع منبع اصلی را پشتیبانی می‌کند:

- `"thermals"` نمایانگر وضعیت حرارتی سراسری کل سیستم است.
- `"cpu"` نمایانگر میانگین فشار واحد پردازش مرکزی (CPU) روی تمام هسته‌های آن است. این وضعیت ممکن است توسط برنامه‌ها و وب‌سایت‌هایی غیر از سایتِ مشاهده‌گر تحت تأثیر قرار گیرد.

برای اینکه ببینید مرورگر شما از کدام نوع منابع پشتیبانی می‌کند، از سرنخ ایستای {{domxref("PressureObserver.knownSources_static", "PressureObserver.knownSources")}} استفاده کنید. توجه داشته باشید که در دسترس بودن ممکن است بسته به سیستم‌عامل و سخت‌افزار شما نیز متفاوت باشد. برای بررسی اینکه آیا مشاهدهٔ فشار امکان‌پذیر است، {{domxref("PressureObserver.observe()", "observe()")}} را فراخوانی کنید و به دنبال خطای `NotSupportedError` بگردید.

## مثال‌ها

### استفاده از ویژگی `source`

در مثال زیر مقدار ویژگی `source` را در تابع بازگشتیِ ناظر فشار ثبت می‌کنیم.

```js
function callback(records) {
  const lastRecord = records[records.length - 1];
  console.log(`Current pressure source: ${lastRecord.source}`);
}

try {
  const observer = new PressureObserver(callback);
  await observer.observe("cpu", {
    sampleInterval: 1000, // 1000ms
  });
} catch (error) {
  // report error setting up the observer
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}