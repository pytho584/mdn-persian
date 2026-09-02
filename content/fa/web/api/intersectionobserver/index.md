---
title: "IntersectionObserver"
---

---
title: IntersectionObserver
slug: Web/API/IntersectionObserver
page-type: web-api-interface
browser-compat: api.IntersectionObserver
---

{{APIRef("Intersection Observer API")}}

رابط **`IntersectionObserver`** از [Intersection Observer API](/en-US/docs/Web/API/Intersection_Observer_API) روشی برای مشاهدهٔ ناهمگام تغییرات در تقاطع یک عنصر هدف با یک عنصر بالادست یا با {{Glossary('viewport')}} سند سطح بالا فراهم می‌کند. به عنصر بالادست یا viewport، ریشه گفته می‌شود.

هنگامی که یک `IntersectionObserver` ساخته می‌شود، برای نظارت بر نسبت‌های مشخصی از دید درون ریشه پیکربندی می‌شود. پس از ایجاد `IntersectionObserver`، این پیکربندی قابل تغییر نیست؛ بنابراین یک شیء observer معین فقط برای نظارت بر تغییرات خاص در میزان دید مفید است. با این حال، می‌توانید چندین عنصر هدف را با همان observer مشاهده کنید.

## Constructor

- {{domxref("IntersectionObserver.IntersectionObserver", "IntersectionObserver()")}}
  - : یک شیء جدید `IntersectionObserver` می‌سازد که هنگام تشخیص عبور دید یک عنصر هدف از یک یا چند آستانه، یک تابع callback مشخص را اجرا می‌کند.

## Instance properties

- {{domxref("IntersectionObserver.delay")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک عدد صحیح که کمترین تأخیر بین اعلان‌های این observer را نشان می‌دهد.
- {{domxref("IntersectionObserver.root")}} {{ReadOnlyInline}}
  - : {{domxref("Element")}} یا {{domxref("Document")}} که مرزهای آن به عنوان جعبه محدودکننده هنگام آزمایش تقاطع استفاده می‌شود. اگر هیچ مقدار `root` به سازنده ارسال نشده باشد یا مقدار آن `null` باشد، viewport سند سطح بالا استفاده می‌شود.
- {{domxref("IntersectionObserver.rootMargin")}} {{ReadOnlyInline}}
  - : یک مستطیل افست که هنگام محاسبه تقاطع‌ها روی {{Glossary('bounding box')}} ریشه اعمال می‌شود و عملاً ریشه را برای اهداف محاسباتی کوچک‌تر یا بزرگ‌تر می‌کند. مقدار بازگردانده‌شده توسط این ویژگی ممکن است با مقداری که هنگام فراخوانی سازنده مشخص شده یکسان نباشد، زیرا ممکن است برای مطابقت با الزامات داخلی تغییر کند. هر افست می‌تواند بر حسب پیکسل (`px`) یا درصد (`%`) بیان شود. مقدار پیش‌فرض «0px 0px 0px 0px» است.
- {{domxref("IntersectionObserver.scrollMargin")}} {{ReadOnlyInline}}
  - : یک مستطیل افست که روی هر {{glossary("scroll container")}} در مسیر از ریشه تقاطع تا هدف اعمال می‌شود و عملاً مستطیل‌های برش مورد استفاده برای محاسبه تقاطع‌ها را کوچک‌تر یا بزرگ‌تر می‌کند. مقدار بازگردانده‌شده توسط این ویژگی ممکن است با مقداری که هنگام فراخوانی سازنده مشخص شده یکسان نباشد.
- {{domxref("IntersectionObserver.thresholds")}} {{ReadOnlyInline}}
  - : فهرستی از آستانه‌ها که به ترتیب عددی صعودی مرتب شده‌اند؛ هر آستانه نسبت مساحت تقاطع به مساحت جعبه محدودکننده یک هدف مشاهده‌شده است. برای یک هدف، زمانی اعلان تولید می‌شود که هر یک از آستانه‌ها برای آن هدف رد شود. اگر هیچ مقداری به سازنده ارسال نشود، از 0 استفاده می‌شود.
- {{domxref("IntersectionObserver.trackVisibility")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک مقدار بولی که نشان می‌دهد آیا این `IntersectionObserver` بررسی می‌کند که دید هدف به خطر نیفتاده باشد.

## Instance methods

- {{domxref("IntersectionObserver.disconnect()")}}
  - : مشاهده هر هدفی توسط شیء `IntersectionObserver` را متوقف می‌کند.
- {{domxref("IntersectionObserver.observe()")}}
  - : به `IntersectionObserver` می‌گوید که یک عنصر هدف را مشاهده کند.
- {{domxref("IntersectionObserver.takeRecords()")}}
  - : آرایه‌ای از اشیاء {{domxref("IntersectionObserverEntry")}} را برای همه اهداف مشاهده‌شده بازمی‌گرداند.
- {{domxref("IntersectionObserver.unobserve()")}}
  - : به `IntersectionObserver` می‌گوید که مشاهده یک عنصر هدف خاص را متوقف کند.

## Examples

```js
const intersectionObserver = new IntersectionObserver((entries) => {
  // If intersectionRatio is 0, the target is out of view
  // and we do not need to do anything.
  if (entries[0].intersectionRatio <= 0) return;

  loadItems(10);
  console.log("Loaded new items");
});
// start observing
intersectionObserver.observe(document.querySelector(".scrollerFooter"));
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref('MutationObserver')}}
- {{domxref('PerformanceObserver')}}
- {{domxref('ResizeObserver')}}