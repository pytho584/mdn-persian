---
title: "LayoutShift"
---

---
title: LayoutShift
slug: Web/API/LayoutShift
page-type: web-api-interface
status:
  - experimental
browser-compat: api.LayoutShift
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

رابطهی `LayoutShift` در [API کارایی](/en-US/docs/Web/API/Performance_API)، بینش‌هایی در مورد پایداری چیدمان صفحات وب بر اساس جابه‌جایی عناصر در صفحه فراهم می‌کند.

## توضیحات

یک تغییر چیدمان زمانی رخ می‌دهد که هر عنصر قابل مشاهده در viewport بین دو فریم موقعیت خود را تغییر دهد. این عناصر به عنوان «ناپایدار» توصیف می‌شوند که نشان‌دهنده‌ی نبود پایداری بصری است.

API ناپایداری چیدمان راهی برای اندازه‌گیری و گزارش این تغییرات چیدمان فراهم می‌کند. همه‌ی ابزارهای اشکال‌زدایی تغییرات چیدمان، از جمله ابزارهای موجود در ابزارهای توسعه‌دهنده‌ی مرورگر، از این API استفاده می‌کنند. این API همچنین می‌تواند برای مشاهده و اشکال‌زدایی تغییرات چیدمان با ثبت اطلاعات در کنسول، ارسال داده‌ها به یک نقطه‌ی پایانی سرور یا به تحلیل‌های صفحه‌ی وب استفاده شود.

ابزارهای کارایی می‌توانند از این API برای محاسبه‌ی نمره‌ی {{glossary("CLS")}} استفاده کنند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

این رابط، ویژگی‌های زیر را از {{domxref("PerformanceEntry")}} با این شرایط گسترش می‌دهد:

- {{domxref("PerformanceEntry.duration")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : همیشه `0` برمی‌گرداند (مفهوم مدت زمان در تغییرات چیدمان کاربرد ندارد).
- {{domxref("PerformanceEntry.entryType")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : همیشه `"layout-shift"` برمی‌گرداند.
- {{domxref("PerformanceEntry.name")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : همیشه `"layout-shift"` برمی‌گرداند.
- {{domxref("PerformanceEntry.startTime")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که زمان شروع تغییر چیدمان را نشان می‌دهد.

این رابط همچنین از ویژگی‌های زیر پشتیبانی می‌کند:

- {{domxref("LayoutShift.value")}} {{Experimental_Inline}}
  - : نمره‌ی تغییر چیدمان را برمی‌گرداند که به صورت کسر تأثیر (کسری از viewport که جابه‌جا شده) ضرب در کسر فاصله (میزان جابه‌جایی به صورت کسری از viewport) محاسبه می‌شود.
- {{domxref("LayoutShift.hadRecentInput")}} {{Experimental_Inline}}
  - : اگر {{domxref("LayoutShift.lastInputTime", "lastInputTime")}} کمتر از ۵۰۰ میلی‌ثانیه در گذشته باشد، `true` برمی‌گرداند.
- {{domxref("LayoutShift.lastInputTime")}} {{Experimental_Inline}}
  - : زمان آخرین ورودی حذف‌کننده (ورودی کاربر که این ورودی را به عنوان کمک‌کننده به نمره‌ی CLS حذف می‌کند) را برمی‌گرداند، یا اگر ورودی حذف‌کننده‌ای رخ نداده باشد `0`.
- {{domxref("LayoutShift.sources")}} {{Experimental_Inline}}
  - : یک آرایه از اشیاء {{domxref("LayoutShiftAttribution")}} با اطلاعاتی درباره عناصری که جابه‌جا شده‌اند برمی‌گرداند.

## روش‌های نمونه

- {{domxref("LayoutShift.toJSON()")}} {{Experimental_Inline}}
  - : ویژگی‌ها را به JSON تبدیل می‌کند.

## مثال‌ها

### ثبت مقادیر تغییر چیدمان

مثال زیر نشان می‌دهد که چگونه تغییرات چیدمان را ضبط کرده و در کنسول ثبت کنید.

```js
const observer = new PerformanceObserver((list) => {
  for (const entry of list.getEntries()) {
    // Count layout shifts without recent user input only
    if (!entry.hadRecentInput) {
      console.log("LayoutShift value:", entry.value);
      if (entry.sources) {
        for (const { node, currentRect, previousRect } of entry.sources)
          console.log("LayoutShift source:", node, {
            currentRect,
            previousRect,
          });
      }
    }
  }
});

observer.observe({ type: "layout-shift", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("LayoutShiftAttribution")}}
- {{glossary("CLS")}}