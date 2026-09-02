---
title: "IntersectionObserver: rootMargin property"
---

---
title: "IntersectionObserver: rootMargin property"
short-title: rootMargin
slug: Web/API/IntersectionObserver/rootMargin
page-type: web-api-instance-property
browser-compat: api.IntersectionObserver.rootMargin
---

{{APIRef("Intersection Observer API")}}

خاصیت فقط‌خواندنی **`rootMargin`** در رابط {{domxref("IntersectionObserver")}} رشته‌ای با نحوی مشابه خاصیت CSS {{cssxref("margin")}} است.

هر ضلع از مستطیلی که `rootMargin` نمایش می‌دهد، پیش از انجام آزمون تقاطع، به ضلع متناظر آن در {{Glossary("bounding box")}} عنصر {{domxref("IntersectionObserver.root", "root")}} اضافه می‌شود.

این امکان را به شما می‌دهد که برای مثال، مرزها را به سمت بیرون تنظیم کنید تا عنصر هدف حتی اگر تعداد مشخصی پیکسل از عرض یا ارتفاع آن بریده شده باشد، ۱۰۰٪ قابل مشاهده در نظر گرفته شود؛ یا اگر لبه‌ای بیش از حد به لبهٔ جعبهٔ محدودکنندهٔ root نزدیک باشد، عنصر هدف را تا حدی پنهان در نظر بگیرید.

برای بررسی عمیق‌تر دربارهٔ `rootMargin` و نحوهٔ کار آن با جعبهٔ محدودکنندهٔ root، به [چگونگی محاسبهٔ تقاطع‌ها](/en-US/docs/Web/API/Intersection_Observer_API#how_intersection_is_calculated) مراجعه کنید.

## مقدار

رشته‌ای، با قالبی مشابه مقدار خاصیت CSS {{cssxref("margin")}}، که شامل آفست‌هایی برای یک یا چند ضلع از جعبهٔ محدودکنندهٔ root است.

این آفست‌ها پیش از محاسبهٔ تقاطع بین مستطیل حاصل و مرزهای عنصر هدف، به مقادیر متناظر در جعبهٔ محدودکنندهٔ root اضافه می‌شوند.

رشته‌ای که این خاصیت برمی‌گرداند ممکن است با رشته‌ای که هنگام نمونه‌سازی {{domxref("IntersectionObserver")}} مشخص شده بود یکسان نباشد. برای مثال، نتیجه همیشه چهار مؤلفه دارد، در حالی که ورودی ممکن است مؤلفه‌های کمتری داشته باشد.

اگر هنگام نمونه‌سازی شیء، `rootMargin` مشخص نشده باشد، مقدار پیش‌فرض آن رشته `"0px 0px 0px 0px"` خواهد بود؛ به این معنی که تقاطع بین مستطیل مرزهای بدون تغییر عنصر ریشه و مرزهای عنصر هدف محاسبه می‌شود. [چگونگی محاسبهٔ تقاطع‌ها](/en-US/docs/Web/API/Intersection_Observer_API#how_intersection_is_calculated) نحوهٔ استفاده از `rootMargin` را با جزئیات بیشتری توصیف می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}