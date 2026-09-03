---
title: PerformanceTimingConfidence
slug: Web/API/PerformanceTimingConfidence
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PerformanceTimingConfidence
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

رابطهٔ **`PerformanceTimingConfidence`** دسترسی به اطلاعاتی را فراهم می‌کند که نشان می‌دهد آیا یک رکورد عملکرد، عملکرد معمولی برنامه را منعکس می‌کند یا احتمالاً تحت تأثیر عوامل بیرونی قرار گرفته است.

برای هر ورودی زمان‌بندی ناوبری، شیء `PerformanceTimingConfidence` از طریق ویژگی {{domxref("PerformanceNavigationTiming.confidence", "confidence")}} در رابط {{domxref("PerformanceNavigationTiming")}} در دسترس است.

## ویژگی‌های نمونه

- {{domxref("PerformanceTimingConfidence.randomizedTriggerRate")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : عددی که نشان می‌دهد هنگام در معرض قرار دادن `value` با چه نسبتی نویز اعمال می‌شود.
- {{domxref("PerformanceTimingConfidence.value")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک مقدار شمارشی که معیار اطمینان کلی به این موضوع را نشان می‌دهد که آیا یک رکورد عملکرد، عملکرد معمولی برنامه را منعکس می‌کند یا احتمالاً تحت تأثیر عوامل بیرونی قرار گرفته است.

## متدهای نمونه

- {{domxref("PerformanceTimingConfidence.toJSON()")}} {{experimental_inline}}
  - : یک نمایش JSON از شیء `PerformanceTimingConfidence` برمی‌گرداند.

## توضیحات

اگر یک وب‌سایت پس از «راه‌اندازی سرد» مرورگر یا بازیابی نشست بارگذاری شده باشد، ممکن است صفحات آن در نتیجهٔ این موضوع کندتر بارگذاری شوند.
این موضوع می‌تواند تفاوت قابل توجهی بین معیارهای داشبوردهای دنیای واقعی و مشاهدات عملکرد در ابزارهای پروفایلینگ صفحه ایجاد کند و در نتیجه برای توسعه‌دهنده دشوار می‌شود که بفهمد آیا یک مشکل عملکرد، نگرانی واقعی است یا یک مقدار پرت ناشی از عوامل بیرونی.

رابط `PerformanceTimingConfidence` به توسعه‌دهندگان امکان می‌دهد با برگرداندن یک تخمین مرورگر (در ویژگی {{domxref("PerformanceTimingConfidence.value", "value")}}) از احتمال اینکه یک رکورد عملکرد بازگشتی، عملکرد معمولی برنامه را نشان دهد، این مشکل را جبران کنند.
این مقدار یا `"low"` است و یا `"high"`، که نشان‌دهندهٔ اطمینان مرورگر به اندازه‌گیری است.

> [!NOTE]
> عواملی مانند CPU در ارزیابی عملکرد مشارکت ندارند. عواملی غیر از «راه‌اندازی سرد» مرورگر و بازیابی نشست نیز ممکن است در به‌روزرسانی‌های آینده در نظر گرفته شوند.

برای کاهش امکان استفاده از مقدار برای اثرانگشت (fingerprinting)، به تخمین نویز اضافه می‌شود؛ به این معنی که `value` برای نسبت مشخصی از نتایج عمداً نادرست خواهد بود.
نرخ اعمال نویز در ویژگی {{domxref("PerformanceTimingConfidence.randomizedTriggerRate", "randomizedTriggerRate")}} داده می‌شود.

از آنجا که این نرخ می‌تواند بین رکوردها متفاوت باشد، برای بازیابی مجموع‌هایی بدون اریبی، به وزندهی به‌ازای هر رکورد نیاز است؛ این کار سازگاری داده‌ها را بهبود می‌بخشد، تعداد خطاهای مرکب را کاهش می‌دهد و به‌طور کلی خط پایه‌ای ایجاد می‌کند که بتوان نتایج اندازه‌گیری‌شده را بر اساس آن ارزیابی کرد.

### استفاده از داده‌ها

برای استخراج اطلاعات معنادار از مقادیر تصادفی‌سازی‌شده، داده‌ها را به صورت زیر استفاده کنید:

1. هنگام جمع‌آوری رکوردهای {{domxref("PerformanceNavigationTiming")}}، برای هر رکورد {{domxref("PerformanceTimingConfidence.randomizedTriggerRate", "randomizedTriggerRate")}} و {{domxref("PerformanceTimingConfidence.value", "value")}} را نیز جمع‌آوری کنید.
2. هنگام محاسبهٔ آمارهایی مانند صدک 75اُم {{glossary("Largest_contentful_paint", "Largest contentful paint (LCP)")}} یا میانگین {{glossary("page load time")}}، به جای میانگین ساده، فرمول‌های وزندهی که در ادامه توضیح داده شده‌اند را اعمال کنید—این کار به شما معیارهای جداگانه و اصلاح‌شده‌ای برای بارگذاری‌های «معمولی» در مقایسه با بارگذاری‌های «تضعیف‌شده» می‌دهد.
3. میانگین/صدک اطمینان «high» را به عنوان «واقعی‌ترین» خط پایهٔ عملکرد خود در نظر بگیرید و از مقدار «low» برای درک اینکه داده‌های معمول در سناریوهای راه‌اندازی سرد چگونه به نظر می‌رسند استفاده کنید.

روش‌های زیر نشان می‌دهند که چگونه می‌توان قبل از محاسبهٔ آمارهای خلاصه بر اساس داده‌های اطمینان، وزندهی مبتنی بر `value` را اعمال کرد.

#### محاسبهٔ میانگین‌های بدون اریبی {#computing_debiased_means}

برای محاسبهٔ میانگین‌های بدون اریبی برای هر دو مقدار [`high` و `low`](/en-US/docs/Web/API/PerformanceTimingConfidence/value#value):

1. برای هر رکورد:
   - فرض کنید `p` برابر با {{domxref("PerformanceTimingConfidence.randomizedTriggerRate", "randomizedTriggerRate")}} رکورد باشد.
   - فرض کنید `c` برابر با {{domxref("PerformanceTimingConfidence.value", "value")}} رکورد باشد.
   - فرض کنید وقتی `c` برابر `high` است، مقدار `R` برابر `1` باشد؛ در غیر این صورت `0`.
2. وزن `w` به‌ازای هر رکورد را بر اساس `c` محاسبه کنید:
   - برای تخمین میانگین `high`: `w = (R - (p / 2)) / (1 - p)`.
   - برای تخمین میانگین `low`: `w = ((1 - R) - (p / 2)) / (1 - p)`.
     > [!NOTE]
     > ممکن است `w` برای برخی رکوردها منفی باشد؛ باید همهٔ رکوردها را نگه دارید.
   - فرض کنید `weighted_duration = duration * w` (به {{domxref("PerformanceEntry.duration", "duration")}} مراجعه کنید).
3. فرض کنید `total_weighted_duration` مجموع مقادیر `weighted_duration` در همهٔ رکوردها باشد.
4. فرض کنید `sum_weights` مجموع مقادیر `w` در همهٔ رکوردها باشد.
5. فرض کنید اگر `sum_weights` نزدیک صفر نباشد، `debiased_mean = total_weighted_duration / sum_weights`.

#### محاسبهٔ صدک‌های بدون اریبی

برای محاسبهٔ صدک‌های بدون اریبی برای هر دو مقدار `high` و `low`:

1. مراحل [محاسبهٔ میانگین‌های بدون اریبی](#computing_debiased_means) را دنبال کنید تا وزن `w` به‌ازای هر رکورد محاسبه شود.
2. فرض کنید `sum_weights` مجموع مقادیر `w` در همهٔ رکوردها باشد.
3. فرض کنید `sorted_records` شامل همهٔ رکوردها باشد که بر اساس `duration` به ترتیب صعودی مرتب شده‌اند.
4. برای صدک مورد نظر (۰ تا ۱۰۰)، `q = percentile / 100.0` را محاسبه کنید.
5. در `sorted_records` پیمایش کنید و برای هر رکورد:
   - وزن تجمعی `cw` را به‌ازای هر رکورد محاسبه کنید: `cw = sum_{i: duration_i <= duration_j} w_i`.
   - تابع توزیع تجمعی بدون اریبی را به‌ازای هر رکورد محاسبه کنید: `cdf = cw / sum_weights`.
6. اولین شاخص `idx` را پیدا کنید که در آن `cdf >= q`.
   - اگر `idx` برابر `0` بود، `duration` مربوط به `sorted_records[0]` را برگردانید.
   - اگر چنین شاخصی وجود نداشت، `duration` مربوط به `sorted_records[n]` را برگردانید.
7. کسر درون‌یابی را محاسبه کنید:
   - فرض کنید `lower_cdf` برابر `cdf` برای `sorted_records[idx-1]` باشد.
   - فرض کنید `upper_cdf` برابر `cdf` برای `sorted_records[idx]` باشد.
   - اگر `lower_cdf = upper_cdf` بود، `duration` مربوط به `sorted_records[idx]` را برگردانید.
   - در غیر این صورت:
     - فرض کنید `ifrac = (q - lower_cdf) / (upper_cdf - lower_cdf)`.
     - فرض کنید `lower_duration` برابر `duration` برای `sorted_records[idx-1]` باشد.
     - فرض کنید `upper_duration` برابر `duration` برای `sorted_records[idx]` باشد.
     - `lower_duration + (upper_duration - lower_duration) * ifrac` را برگردانید.

## مثال‌ها

### استفادهٔ پایه

این مثال از یک {{domxref("PerformanceObserver")}} برای دریافت داده‌های اطمینان از ورودی‌های مشاهده‌شدهٔ {{domxref("PerformanceNavigationTiming")}} استفاده می‌کند.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(
      `${entry.name} confidence: ${entry.confidence.value}`,
      `Trigger rate: ${entry.confidence.randomizedTriggerRate}`,
    );
  });
});

observer.observe({ type: "navigation", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceNavigationTiming")}}