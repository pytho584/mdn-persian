---
title: "Animation"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation"
translated_by: "n8n + AI"
---

---
title: Animation
slug: Web/API/Animation
page-type: web-api-interface
browser-compat: api.Animation
---

{{ APIRef("Web Animations") }}

رابط **`Animation`** در [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) نمایانگر یک پخش‌کننده انیمیشن واحد است و کنترل‌های پخش و یک خط زمانی برای یک گره یا منبع انیمیشن فراهم می‌کند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("Animation.Animation()", "Animation()")}}
  - : یک نمونه جدید از شیء `Animation` ایجاد می‌کند.

## ویژگی‌های نمونه

- {{domxref("Animation.currentTime")}}
  - : مقدار زمان فعلی انیمیشن بر حسب میلی‌ثانیه، چه در حال اجرا باشد چه مکث شده باشد. اگر انیمیشن فاقد {{domxref("AnimationTimeline", "timeline")}} باشد، غیرفعال باشد یا هنوز پخش نشده باشد، مقدار آن `null` است.
- {{domxref("Animation.effect")}}
  - : {{domxref("AnimationEffect")}} مرتبط با این انیمیشن را دریافت و تنظیم می‌کند. این معمولاً یک شیء {{domxref("KeyframeEffect")}} است.
- {{domxref("Animation.finished")}} {{ReadOnlyInline}}
  - : Promise تمام‌شده فعلی این انیمیشن را برمی‌گرداند.
- {{domxref("Animation.id")}}
  - : `String` مورد استفاده برای شناسایی انیمیشن را دریافت و تنظیم می‌کند.
- {{domxref("Animation.overallProgress")}} {{ReadOnlyInline}}
  - : عددی بین `0` و `1` برمی‌گرداند که پیشرفت کلی انیمیشن را به سمت حالت تمام‌شده آن نشان می‌دهد.
- {{domxref("Animation.pending")}} {{ReadOnlyInline}}
  - : نشان می‌دهد که آیا انیمیشن در حال حاضر منتظر یک عملیات ناهمگام مانند شروع پخش یا مکث کردن یک انیمیشن در حال اجرا است.
- {{domxref("Animation.playState")}} {{ReadOnlyInline}}
  - : یک مقدار شمارشی (enumerated) را برمی‌گرداند که وضعیت پخش یک انیمیشن را توصیف می‌کند.
- {{domxref("Animation.playbackRate")}}
  - : نرخ پخش انیمیشن را دریافت یا تنظیم می‌کند.
- {{domxref("Animation.ready")}} {{ReadOnlyInline}}
  - : Promise آماده فعلی این انیمیشن را برمی‌گرداند.
- {{domxref("Animation.replaceState")}} {{ReadOnlyInline}}
  - : نشان می‌دهد که آیا انیمیشن فعال است، پس از جایگزین شدن با انیمیشن دیگر به‌طور خودکار حذف شده است، یا با فراخوانی {{domxref("Animation.persist()")}} به‌طور صریح حفظ شده است.
- {{domxref("Animation.startTime")}}
  - : زمان برنامه‌ریزی‌شده برای شروع پخش یک انیمیشن را دریافت یا تنظیم می‌کند.
- {{domxref("Animation.timeline")}}
  - : {{domxref("AnimationTimeline", "timeline")}} مرتبط با این انیمیشن را دریافت یا تنظیم می‌کند.

## متدهای نمونه

- {{domxref("Animation.cancel()")}}
  - : همه {{domxref("KeyframeEffect", "keyframeEffects")}} ایجادشده توسط این انیمیشن را پاک می‌کند و پخش آن را متوقف می‌کند.
- {{domxref("Animation.commitStyles()")}}
  - : وضعیت استایل فعلی یک انیمیشن را به عنصر در حال انیمیشن اعمال می‌کند، حتی پس از حذف آن انیمیشن. این کار باعث می‌شود وضعیت استایل فعلی به شکل ویژگی‌هایی در یک ویژگی `style` به عنصر در حال انیمیشن نوشته شود.
- {{domxref("Animation.finish()")}}
  - : بسته به اینکه انیمیشن در حال پخش است یا در حال معکوس شدن، به یکی از انتهای انیمیشن می‌رود.
- {{domxref("Animation.pause()")}}
  - : پخش یک انیمیشن را به حالت تعلیق درمی‌آورد.
- {{domxref("Animation.persist()")}}
  - : به‌طور صریح یک انیمیشن را حفظ می‌کند و از [حذف خودکار](/en-US/docs/Web/API/Web_Animations_API/Using_the_Web_Animations_API#automatically_removing_filling_animations) آن زمانی که انیمیشن دیگری جایگزینش می‌شود، جلوگیری می‌کند.
- {{domxref("Animation.play()")}}
  - : پخش یک انیمیشن را شروع یا از سر می‌گیرد، یا اگر انیمیشن قبلاً تمام شده باشد، دوباره آن را آغاز می‌کند.
- {{domxref("Animation.reverse()")}}
  - : جهت پخش را معکوس می‌کند و در شروع انیمیشن متوقف می‌شود. اگر انیمیشن تمام شده باشد یا پخش نشده باشد، از انتها به ابتدا پخش می‌شود.
- {{domxref("Animation.updatePlaybackRate()")}}
  - : سرعت یک انیمیشن را پس از همگام‌سازی اولیه موقعیت پخش آن تنظیم می‌کند.

## رویدادها

- {{domxref("Animation.cancel_event", "cancel")}}
  - : زمانی رخ می‌دهد که متد {{domxref("Animation.cancel()")}} فراخوانی شود یا زمانی که انیمیشن از حالتی دیگر وارد حالت پخش `"idle"` شود.
- {{domxref("Animation.finish_event", "finish")}}
  - : زمانی رخ می‌دهد که پخش انیمیشن به پایان برسد.
- {{domxref("animation.remove_event", "remove")}}
  - : زمانی رخ می‌دهد که انیمیشن توسط مرورگر [به‌طور خودکار حذف](/en-US/docs/Web/API/Web_Animations_API/Using_the_Web_Animations_API#automatically_removing_filling_animations) شود.

## نگرانی‌های دسترس‌پذیری

انیمیشن‌های چشمک‌زن و فلاش‌زننده می‌توانند برای افراد دارای نگرانی‌های شناختی مانند اختلال کم‌توجهی-بیش‌فعالی (ADHD) مشکل‌ساز باشند. علاوه بر این، انواع خاصی از حرکت می‌توانند محرکی برای اختلالات دهلیزی، صرع، میگرن و حساسیت اسکوتوپیک باشند.

ارائه سازوکاری برای مکث یا غیرفعال کردن انیمیشن را در نظر بگیرید، همچنین از [Reduced Motion Media Query](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-motion) (یا معادل [user agent client hint](/en-US/docs/Web/HTTP/Guides/Client_hints#user_agent_client_hints) {{HTTPHeader("Sec-CH-Prefers-Reduced-Motion")}}) برای ایجاد تجربه‌ای مکمل برای کاربرانی که ترجیح خود را برای عدم وجود تجربه‌های انیمیشنی ابراز کرده‌اند، استفاده کنید.

- [Designing Safer Web Animation For Motion Sensitivity · An A List Apart Article](https://alistapart.com/article/designing-safer-web-animation-for-motion-sensitivity/)
- [An Introduction to the Reduced Motion Media Query | CSS-Tricks](https://css-tricks.com/introduction-reduced-motion-media-query/)
- [Responsive Design for Motion | WebKit](https://webkit.org/blog/7551/responsive-design-for-motion/)
- [MDN Understanding WCAG, Guideline 2.2 explanations](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Operable#guideline_2.2_%e2%80%94_enough_time_provide_users_enough_time_to_read_and_use_content)
- [Understanding Success Criterion 2.2.2 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-pause.html)

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)