---
title: Popover API
slug: Web/API/Popover_API
page-type: web-api-overview
browser-compat:
  - api.HTMLElement.popover
  - api.HTMLElement.beforetoggle_event.popover_elements
  - api.HTMLElement.toggle_event.popover_elements
---

{{DefaultAPISidebar("Popover API")}}

**Popover API** سازوکاری استاندارد، سازگار و انعطاف‌پذیر در اختیار توسعه‌دهندگان قرار می‌دهد تا محتوای پاپاور را روی سایر محتوای صفحه نمایش دهند. محتوای پاپاور را می‌توان با ویژگی‌های HTML یا از طریق جاوااسکریپت کنترل کرد.

## مفاهیم و کاربرد

یک الگوی بسیار رایج در وب این است که محتوایی روی محتوای دیگر نمایش داده می‌شود تا توجه کاربر به اطلاعات مهم یا اقداماتی که باید انجام شوند جلب شود. برای چنین محتوایی نام‌های مختلفی به کار می‌رود: overlay، popup، popover، dialog و جز این‌ها. در این مستندات، همهٔ این‌ها را «پاپاور» می‌نامیم. به‌طور کلی، این محتواها می‌توانند:

- **modal**: به این معنا که وقتی پاپاور نمایش داده می‌شود، بقیهٔ صفحه تا زمانی که به نحوی با پاپاور تعامل نشود (مثلاً انتخاب مهمی انجام نشود) غیرقابل‌تعامل می‌ماند.
- **non-modal**: به این معنا که وقتی پاپاور نمایش داده می‌شود، بقیهٔ صفحه همچنان قابل‌تعامل است.

پاپاورهای ساخته‌شده با Popover API همیشه غیرمودال هستند. اگر می‌خواهید یک پاپاور مودال ایجاد کنید، راه درست استفاده از عنصر {{htmlelement("dialog")}} است. بین این دو هم‌پوشانی قابل‌توجهی وجود دارد؛ برای نمونه، ممکن است بخواهید پاپاوری بسازید که ماندگار است ولی آن را با HTML کنترل کنید. اگر می‌خواهید کنترل پاپاور را با معنای dialog ترکیب کنید، می‌توانید عنصر `<dialog>` را به پاپاور تبدیل کنید (`<dialog popover>` کاملاً معتبر است).

مهم‌ترین کاربردهای Popover API شامل عناصر تعاملی مانند منوهای عملیات، اعلان‌های «toast» سفارشی، پیشنهادهای عناصر فرم، انتخاب‌گرهای محتوا یا رابط‌های کاربری آموزشی است.

پاپاورها را می‌توان به چند روش ساخت:

- از طریق مجموعه‌ای از ویژگی‌های جدید HTML. یک پاپاور ساده که دکمهٔ تغییر وضعیت (toggle) دارد را می‌توان با کد زیر ایجاد کرد:

  ```html
  <button popovertarget="mypopover">Toggle the popover</button>
  <div id="mypopover" popover>Popover content</div>
  ```

- از طریق یک API جاوااسکریپتی. مثلاً {{domxref("HTMLElement.togglePopover()")}} می‌تواند برای جابه‌جا کردن وضعیت پاپاور بین نمایش و پنهان بودن به کار رود.

Popover API همچنین رویدادهایی برای واکنش به تغییر وضعیت پاپاور و امکانات CSS برای استایل‌دهی به پاپاورها فراهم می‌کند. برای راهنمای دقیق API، مستندات [استفاده از Popover API](/en-US/docs/Web/API/Popover_API/Using) را ببینید.

یک قابلیت مرتبط به نام **interest invoker** نیز می‌تواند بدون نیاز به جاوااسکریپت، پاپاورها را هنگام hover یا فوکوس نمایش دهد. برای اطلاعات بیشتر به [استفاده از interest invoker](/en-US/docs/Web/API/Popover_API/Using_interest_invokers) مراجعه کنید.

## ویژگی‌های HTML

- [`interestfor`](/en-US/docs/Web/HTML/Reference/Elements/button#interestfor) {{experimental_inline}}
  - : عنصر HTML {{htmlelement("a")}}، {{htmlelement("button")}} یا {{htmlelement("area")}} یا عنصر [`<a>`](/en-US/docs/Web/SVG/Reference/Element/a) در SVG را به‌عنوان interest invoker تعریف می‌کند. مقدار این ویژگی، `id` عنصر هدف است؛ عنصری که وقتی نسبت به عنصر invoker علاقه (interest) ابراز شود یا از بین برود، به‌گونه‌ای (معمولاً نمایش یا پنهان‌سازی) تحت تأثیر قرار می‌گیرد.

- [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover)
  - : یک ویژگی سراسری که عنصر را به یک پاپاور تبدیل می‌کند؛ مقدار آن یکی از حالت‌های پاپاور (`"auto"`، `"hint"` یا `"manual"`) است.

- [`popovertarget`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertarget)
  - : عنصر {{htmlelement("button")}} یا {{htmlelement("input")}} را به دکمهٔ کنترل پاپاور تبدیل می‌کند؛ مقدار آن شناسهٔ عنصر پاپاوری است که باید کنترل شود.

- [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction)
  - : عملیاتی را که باید روی عنصر پاپاورِ کنترل‌شده توسط یک {{htmlelement("button")}} یا {{htmlelement("input")}} کنترلی انجام شود (`"hide"`، `"show"` یا `"toggle"`) مشخص می‌کند.

## امکانات CSS

- {{cssxref("::backdrop")}}
  - : شبه‌عنصر `::backdrop` عنصری تمام‌صفحه است که دقیقاً پشت عناصر پاپاور قرار می‌گیرد و در صورت نیاز امکان افزودن افکت به محتوای پشت پاپاور را فراهم می‌کند (مثلاً محوکردن آن).

- {{cssxref("interest-delay")}}، {{cssxref("interest-delay-start")}} و {{cssxref("interest-delay-end")}} {{experimental_inline}}
  - : ویژگی ترکیبی `interest-delay` و ویژگی‌های جزء (longhand) مرتبط با آن، یعنی `interest-delay-start` و `interest-delay-end`، برای افزودن تأخیر بین ابراز علاقه یا از دست رفتن آن توسط کاربر و واکنش مرورگر به این تغییر به کار می‌روند.

- {{cssxref(":interest-source")}} و {{cssxref(":interest-target")}}
  - : این انتخاب‌گرها را می‌توان برای اعمال استایل به‌ترتیب روی interest invoker و عنصر هدفِ مرتبط با آن، فقط وقتی که علاقه (interest) ابراز شده است به کار برد.

- {{cssxref(":popover-open")}}
  - : شبه‌کلاس `:popover-open` فقط زمانی با یک عنصر پاپاور مطابقت می‌کند که آن عنصر در حالت نمایش باشد؛ می‌توان از آن برای استایل‌دهی به عناصر پاپاور هنگام نمایش استفاده کرد.

## رابط‌ها

- {{domxref("InterestEvent")}} {{experimental_inline}}
  - : شیء رویداد برای رویدادهای {{domxref("HTMLElement.interest_event", "interest")}} و {{domxref("HTMLElement.loseinterest_event", "loseinterest")}}. این شیء شامل خصوصیت `source` است که ارجاعی به عنصر interest invoker مرتبط را نگه می‌دارد.

- {{domxref("ToggleEvent")}}
  - : نمایانگر رویدادی است که هنگام جابه‌جایی وضعیت یک عنصر پاپاور بین نمایش و پنهان‌بودن فعال می‌شود. این شیء، شیء رویداد برای رویدادهای {{domxref("HTMLElement.beforetoggle_event", "beforetoggle")}} و {{domxref("HTMLElement.toggle_event", "toggle")}} است که هنگام تغییر وضعیت پاپاورها روی آن‌ها فعال می‌شوند.

## توسعه‌های اعمال‌شده بر سایر رابط‌ها

### خصوصیت‌های نمونه

- {{domxref("HTMLButtonElement.interestForElement", "interestForElement")}} {{experimental_inline}}
  - : ارجاع به عنصر هدفِ یک interest invoker را می‌خواند یا تنظیم می‌کند. اگر یک interest invoker در HTML یا SVG در ویژگیِ `interestfor` خود به عنصر هدفی ارجاع دهد، آن عنصر در خصوصیتِ `interestForElement` شیء DOM متناظر ارجاع داده می‌شود. این خصوصیت در رابط‌های {{domxref("HTMLButtonElement")}}، {{domxref("HTMLAnchorElement")}}، {{domxref("HTMLAreaElement")}} و {{domxref("SVGAElement")}} در دسترس است.

- {{domxref("HTMLElement.popover")}}
  - : وضعیت پاپاورِ یک عنصر را از طریق جاوااسکریپت (`"auto"`، `"hint"` یا `"manual"`) می‌خواند و تنظیم می‌کند و می‌توان از آن برای تشخیص پشتیبانی مرورگر از این قابلیت استفاده کرد. مقدار ویژگی سراسری [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) در HTML را منعکس می‌کند.

- {{domxref("HTMLButtonElement.popoverTargetElement")}} و {{domxref("HTMLInputElement.popoverTargetElement")}}
  - : عنصر پاپاوری را که توسط کنترل‌کننده مدیریت می‌شود می‌خوانند یا تنظیم می‌کنند. این خصوصیت‌ها معادل جاوااسکریپتیِ ویژگی HTML [`popovertarget`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertarget) هستند.

- {{domxref("HTMLButtonElement.popoverTargetAction")}} و {{domxref("HTMLInputElement.popoverTargetAction")}}
  - : عملیاتی که باید روی عنصر پاپاورِ کنترل‌شده توسط کنترل‌کننده انجام شود (`"hide"`، `"show"` یا `"toggle"`) را می‌خوانند یا تنظیم می‌کنند. این خصوصیت‌ها مقدار ویژگی HTML [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction) را منعکس می‌کنند.

### متدهای نمونه

- {{domxref("HTMLElement.hidePopover()")}}
  - : یک عنصر پاپاور را با حذف کردن از لایهٔ بالا (top layer) و اعمال `display: none` پنهان می‌کند.

- {{domxref("HTMLElement.showPopover()")}}
  - : یک عنصر پاپاور را با افزودن به لایهٔ بالا (top layer) نمایش می‌دهد.

- {{domxref("HTMLElement.togglePopover()")}}
  - : وضعیت یک عنصر پاپاور را بین حالت نمایش و حالت پنهان جابه‌جا می‌کند.

### رویدادها

- رویداد {{domxref("HTMLElement.beforetoggle_event","beforetoggle")}}
  - : دقیقاً پیش از تغییر وضعیت یک عنصر پاپاور بین نمایش و پنهان‌بودن (یا برعکس) فعال می‌شود. می‌توان از آن برای جلوگیری از باز شدن پاپاور یا به‌روزرسانی عناصر دیگری که باید بر اساس وضعیت پاپاور فعال شوند استفاده کرد.

- رویداد {{domxref("HTMLElement.toggle_event", "toggle")}}
  - : دقیقاً پس از تغییر وضعیت یک عنصر پاپاور بین نمایش و پنهان‌بودن (یا برعکس) فعال می‌شود.

- {{domxref("HTMLElement.interest_event", "interest")}} {{experimental_inline}}
  - : زمانی که علاقه (interest) ابراز می‌شود روی عنصر هدفِ یک interest invoker فعال می‌شود و امکان اجرای کد در پاسخ به آن را فراهم می‌کند.

- {{domxref("HTMLElement.loseinterest_event", "loseinterest")}} {{experimental_inline}}
  - : زمانی که علاقه (interest) از بین می‌رود روی عنصر هدفِ یک interest invoker فعال می‌شود و امکان اجرای کد در پاسخ به آن را فراهم می‌کند.

## نمونه‌ها

- مجموعه [نمونه‌های Popover API](https://mdn.github.io/dom-examples/popover-api/) را ببینید.
- مجموعه [نمونه‌های interest invoker](https://mdn.github.io/dom-examples/interest-invokers/) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) — ویژگی سراسری HTML
- [`popovertarget`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertarget) — ویژگی HTML
- [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction) — ویژگی HTML
- {{cssxref("::backdrop")}} — شبه‌عنصر CSS
- {{cssxref(":popover-open")}} — شبه‌کلاس CSS