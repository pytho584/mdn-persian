```
---
title: LargestContentfulPaint
slug: Web/API/LargestContentfulPaint
page-type: web-api-interface
browser-compat: api.LargestContentfulPaint
---

{{APIRef("Performance API")}}

رابط `LargestContentfulPaint` اطلاعات زمان‌بندی مربوط به paint بزرگ‌ترین تصویر یا متن در یک صفحه وب را، پیش از هرگونه ورودی کاربر، فراهم می‌کند.

## توضیحات

لحظهٔ کلیدی که این رابط فراهم می‌کند، معیار {{Glossary("Largest Contentful Paint")}} (LCP) است. این رابط، زمان رندر بزرگ‌ترین تصویر یا بلوک متنی را که در viewport قابل مشاهده است و از لحظهٔ شروع بارگذاری صفحه ثبت شده، ارائه می‌دهد. عناصر زیر هنگام تعیین LCP در نظر گرفته می‌شوند:

- عنصرهای {{HTMLElement("img")}}.
- عنصرهای [`<image>`](/en-US/docs/Web/SVG/Reference/Element/image) درون یک SVG.
- تصویرهای پوسترِ (poster) عنصرهای {{HTMLElement("video")}}.
- عنصرهایی که دارای {{cssxref("background-image")}} هستند.
- گروه‌هایی از گره‌های متنی، مانند {{HTMLElement("p")}}.

برای اندازه‌گیری زمان رندرِ سایر عناصر، از رابط {{domxref("PerformanceElementTiming")}} استفاده کنید.

سایر لحظه‌های کلیدیِ paint نیز توسط رابط {{domxref("PerformancePaintTiming")}} ارائه می‌شوند:

- {{Glossary("First Paint")}} (FP): زمانی که هر چیزی رندر می‌شود. توجه داشته باشید که علامت‌گذاریِ اولین paint اختیاری است و همهٔ عامل‌های کاربر (user agent) آن را گزارش نمی‌دهند.
- {{Glossary("First Contentful Paint")}} (FCP): زمانی که نخستین بخش از محتوای متنی یا تصویری DOM رندر می‌شود.

`LargestContentfulPaint` از {{domxref("PerformanceEntry")}} ارث می‌برد.

{{InheritanceDiagram}}

برای به‌دست آوردن اندازه‌گیری دقیق زمان رندر منابع متقاطع-خاستگاه (cross-origin)، هدر {{httpheader("Timing-Allow-Origin")}} را تنظیم کنید.

برای جزئیات بیشتر، به [زمان رندر تصویر متقاطع-خاستگاه](/en-US/docs/Web/API/LargestContentfulPaint/renderTime#cross-origin_image_render_time) و [استفاده از startTime به‌جای renderTime](/en-US/docs/Web/API/LargestContentfulPaint/renderTime#use_starttime_over_rendertime) مراجعه کنید.

## ویژگی‌های نمونه

این رابط ویژگی‌های زیر را مستقیماً تعریف می‌کند:

- {{domxref("LargestContentfulPaint.element")}} {{ReadOnlyInline}}
  - : عنصری که در حال حاضر بزرگ‌ترین contentful paint است.
- {{domxref("LargestContentfulPaint.renderTime")}} {{ReadOnlyInline}}
  - : زمانی که عنصر روی صفحه رندر شد. اگر عنصر تصویری متقاطع-خاستگاه باشد که بدون هدر `Timing-Allow-Origin` بارگذاری شده باشد، این مقدار ممکن است با دقت کاهش‌یافته (coarsened) ارائه شود.
- {{domxref("LargestContentfulPaint.loadTime")}} {{ReadOnlyInline}}
  - : زمانی که عنصر بارگذاری شد.
- {{domxref("LargestContentfulPaint.size")}} {{ReadOnlyInline}}
  - : اندازهٔ ذاتی (intrinsic) عنصر که به‌صورت مساحت (عرض × ارتفاع) بازگردانده می‌شود.
- {{domxref("LargestContentfulPaint.id")}} {{ReadOnlyInline}}
  - : شناسه (id) عنصر. اگر شناسه‌ای وجود نداشته باشد، این ویژگی یک رشتهٔ خالی بازمی‌گرداند.
- {{domxref("LargestContentfulPaint.paintTime")}}
  - : یک {{domxref("DOMHighResTimeStamp","timestamp")}} را بازمی‌گرداند که نشان‌دهندهٔ پایان فاز رندر و شروع فاز paint است.
- {{domxref("LargestContentfulPaint.presentationTime")}}
  - : یک {{domxref("DOMHighResTimeStamp","timestamp")}} را بازمی‌گرداند که نشان‌دهندهٔ زمانی است که پیکسل‌های ترسیم‌شده (painted pixels) واقعاً روی صفحه رسم شدند.
- {{domxref("LargestContentfulPaint.url")}} {{ReadOnlyInline}}
  - : اگر عنصر یک تصویر باشد، URL درخواستِ تصویر را بازمی‌گرداند.

همچنین ویژگی‌های زیر را از {{domxref("PerformanceEntry")}} گسترش می‌دهد و آن‌ها را به‌شکل زیر مشخص و محدود می‌کند:

- {{domxref("PerformanceEntry.entryType")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : مقدار `"largest-contentful-paint"` را بازمی‌گرداند.
- {{domxref("PerformanceEntry.name")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : همیشه یک رشتهٔ خالی بازمی‌گرداند.
- {{domxref("PerformanceEntry.startTime")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : مقدار ویژگی {{domxref("LargestContentfulPaint.renderTime", "renderTime")}} این ورودی را بازمی‌گرداند.
- {{domxref("PerformanceEntry.duration")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : مقدار `0` را بازمی‌گرداند، زیرا `duration` برای این رابط قابل استفاده نیست.

## متدهای نمونه

_این رابط همچنین متدهایی را از {{domxref("PerformanceEntry")}} به ارث می‌برد._

- {{domxref("LargestContentfulPaint.toJSON()")}}
  - : یک نمایش JSON از شیء `LargestContentfulPaint` بازمی‌گرداند.

## مثال‌ها

### مشاهدهٔ بزرگ‌ترین contentful paint

در مثال زیر، یک {{domxref("PerformanceObserver")}} ثبت می‌شود تا بزرگ‌ترین contentful paint را هنگام بارگذاریِ صفحه به دست آورد. از پرچم `buffered` برای دسترسی به داده‌های پیش از ایجاد observer استفاده می‌شود.

API مربوط به LCP تمام محتوایی را که پیدا می‌کند تحلیل می‌کند (از جمله محتوایی که از DOM حذف شده است). وقتی محتوای بزرگ‌تر جدیدی پیدا شود، یک ورودی جدید می‌سازد. وقتی رویدادهای scroll یا input رخ دهند، جستجو برای محتوای بزرگ‌تر متوقف می‌شود، زیرا این رویدادها احتمالاً محتوای جدیدی را وارد وب‌سایت می‌کنند. بنابراین، LCP آخرین ورودی عملکردی است که observer گزارش می‌کند.

```js
const observer = new PerformanceObserver((list) => {
  const entries = list.getEntries();
  const lastEntry = entries[entries.length - 1]; // Use the latest LCP candidate
  console.log("LCP:", lastEntry.startTime);
  console.log(lastEntry);
});
observer.observe({ type: "largest-contentful-paint", buffered: true });
```

### مشاهدهٔ زمان‌های جداگانهٔ paint و presentation

ویژگی‌های `paintTime` و `presentationTime` به شما امکان می‌دهند زمان‌های مشخصِ شروعِ فاز paint و رسمِ پیکسل‌های ترسیم‌شده روی صفحه را بازیابی کنید. `paintTime` به‌طور گسترده‌ای بین مرورگرها interoperable است، در حالی که `presentationTime` وابسته به پیاده‌سازی است.

این مثال بر پایهٔ مثال قبلیِ observer ساخته شده است و نشان می‌دهد که چگونه پشتیبانی از `paintTime` و `presentationTime` بررسی شود و در صورت وجود، این مقادیر بازیابی شوند. در مرورگرهایی که از این ویژگی‌ها پشتیبانی نمی‌کنند، کد بسته به اینکه کدام یک پشتیبانی می‌شود، `renderTime` یا `loadTime` را بازیابی می‌کند.

```js
const observer = new PerformanceObserver((list) => {
  const entries = list.getEntries();
  const lastEntry = entries[entries.length - 1]; // Use the latest LCP candidate
  if (lastEntry.presentationTime) {
    console.log(
      "LCP paintTime:",
      lastEntry.paintTime,
      "LCP presentationTime:",
      lastEntry.presentationTime,
    );
  } else if (lastEntry.paintTime) {
    console.log("LCP paintTime:", lastEntry.paintTime);
  } else if (lastEntry.renderTime) {
    console.log("LCP renderTime:", lastEntry.renderTime);
  } else {
    console.log("LCP loadTime:", lastEntry.loadTime);
  }
});
observer.observe({ type: "largest-contentful-paint", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{Glossary("Largest Contentful Paint")}}
- {{Glossary("First Contentful Paint")}}
- {{Glossary("First Paint")}}
```