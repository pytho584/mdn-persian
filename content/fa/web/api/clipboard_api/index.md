---
title: "Clipboard API"
---

---
title: Clipboard API
slug: Web/API/Clipboard_API
page-type: web-api-overview
browser-compat:
  - api.Clipboard
  - api.ClipboardChangeEvent
  - api.ClipboardEvent
  - api.ClipboardItem
---

{{DefaultAPISidebar("Clipboard API")}}

**Clipboard API** توانایی پاسخ به دستورات کلیپ‌بورد (برش، کپی و چسباندن) و همچنین خواندن و نوشتن ناهمگام (async) در کلیپ‌بورد سیستم را فراهم می‌کند.

> [!NOTE]
> برای دسترسی به کلیپ‌بورد، از این API به جای متد منسوخ شده {{domxref("document.execCommand()")}} استفاده کنید.

> [!NOTE]
> این API در [Web Workers](/en-US/docs/Web/API/Web_Workers_API) _در دسترس نیست_ (از طریق {{domxref("WorkerNavigator")}} در معرض دید قرار نمی‌گیرد).

## مفاهیم و کاربرد

_کلیپ‌بورد سیستم_ یک بافر داده (data buffer) متعلق به سیستم‌عامل میزبان مرورگر است که برای ذخیره‌سازی موقت داده‌ها و/یا انتقال داده‌ها بین اسناد یا برنامه‌ها استفاده می‌شود. این معمولاً به عنوان یک [بافر داده](https://en.wikipedia.org/wiki/Data_buffer) موقت و ناشناس پیاده‌سازی می‌شود که گاهی _بافر چسباندن_ (paste buffer) نامیده می‌شود و از طریق واسط‌های برنامه‌نویسی تعریف‌شده، از اکثر یا همه برنامه‌های درون محیط قابل دسترسی است.

Clipboard API به کاربران امکان می‌دهد تا متن و انواع دیگر داده‌ها را به صورت برنامه‌ریزی‌شده (programmatic) از کلیپ‌بورد سیستم بخوانند و بنویسند، البته در [زمینه‌های امن (secure contexts)](/en-US/docs/Web/Security/Defenses/Secure_Contexts) و به شرطی که کاربر معیارهای ذکر شده در بخش [ملاحظات امنیتی](#security_considerations) را برآورده کرده باشد.

رویدادها در نتیجه عملیات {{domxref("Element/cut_event", "cut")}} (برش)، {{domxref("Element/copy_event", "copy")}} (کپی) و {{domxref("Element/paste_event", "paste")}} (چسباندن) که کلیپ‌بورد را تغییر می‌دهند، فعال می‌شوند. این رویدادها دارای یک عملکرد پیش‌فرض هستند، برای مثال عملکرد `copy` به طور پیش‌فرض انتخاب فعلی را در کلیپ‌بورد سیستم کپی می‌کند. عملکرد پیش‌فرض می‌تواند توسط کنترل‌کننده رویداد لغو شود — برای اطلاعات بیشتر به هر یک از رویدادها مراجعه کنید.

همچنین یک رویداد {{domxref("Clipboard.clipboardchange_event","clipboardchange")}} وجود دارد که مستقیماً روی شیء {{domxref("Clipboard")}} هر زمان که محتویات کلیپ‌بورد سیستم تغییر کند، فعال می‌شود. این برای اطلاع‌رسانی به برنامه‌ها درباره تغییر در کلیپ‌بورد سیستم مفید است، مثلاً اگر برنامه‌ها کلیپ‌بورد مخصوص خود را داشته باشند که باید همگام‌سازی شود.

## واسط‌ها

- {{domxref("Clipboard")}} {{securecontext_inline}}
  - : یک واسط برای خواندن و نوشتن متن و داده به/از کلیپ‌بورد سیستم فراهم می‌کند. مشخصات فنی از این به عنوان 'Async Clipboard API' یاد می‌کند.
- {{domxref("ClipboardChangeEvent")}}
  - : نمایانگر رویدادهایی است که هر زمان محتویات کلیپ‌بورد سیستم تغییر کند، فعال می‌شوند.
- {{domxref("ClipboardEvent")}}
  - : نمایانگر رویدادهایی است که اطلاعات مربوط به تغییر کلیپ‌بورد را ارائه می‌دهند، یعنی رویدادهای {{domxref("Element/cut_event", "cut")}}، {{domxref("Element/copy_event", "copy")}} و {{domxref("Element/paste_event", "paste")}}. مشخصات فنی از این به عنوان 'Clipboard Event API' یاد می‌کند.
- {{domxref("ClipboardItem")}} {{securecontext_inline}}
  - : نمایانگر یک قالب آیتم واحد است که هنگام خواندن یا نوشتن داده استفاده می‌شود.

### افزونه‌های سایر واسط‌ها

Clipboard API واسط‌های زیر را با افزودن ویژگی‌های ذکر شده گسترش می‌دهد.

- {{domxref("Navigator.clipboard")}} {{readonlyinline}} {{securecontext_inline}}
  - : یک شیء {{domxref("Clipboard")}} برمی‌گرداند که دسترسی خواندن و نوشتن به کلیپ‌بورد سیستم را فراهم می‌کند.
- رویداد `Element` [`copy`](/en-US/docs/Web/API/Element/copy_event)
  - : رویدادی که هر زمان کاربر یک عمل کپی را آغاز کند، فعال می‌شود.
- رویداد `Element` [`cut`](/en-US/docs/Web/API/Element/cut_event)
  - : رویدادی که هر زمان کاربر یک عمل برش را آغاز کند، فعال می‌شود.
- رویداد `Element` [`paste`](/en-US/docs/Web/API/Element/paste_event)
  - : رویدادی که هر زمان کاربر یک عمل چسباندن را آغاز کند، فعال می‌شود.

## ملاحظات امنیتی

Clipboard API به کاربران امکان می‌دهد تا متن و انواع دیگر داده‌ها را به صورت برنامه‌ریزی‌شده از کلیپ‌بورد سیستم بخوانند و بنویسند، البته در [زمینه‌های امن (secure contexts)](/en-US/docs/Web/Security/Defenses/Secure_Contexts).

هنگام خواندن از کلیپ‌بورد، مشخصات فنی ایجاب می‌کند که کاربر اخیراً با صفحه تعامل داشته باشد ([فعال‌سازی موقت کاربر (transient user activation)](/en-US/docs/Web/Security/Defenses/User_activation)) و فراخوانی در نتیجه تعامل کاربر با یک «عنصر چسباندن» مرورگر یا سیستم‌عامل (مانند انتخاب «چسباندن» در منوی زمینه بومی) انجام شود. در عمل، مرورگرها اغلب عملیات خواندنی را که این الزامات را برآورده نمی‌کنند مجاز می‌دانند، اما در عوض الزامات دیگری (مانند مجوز یا درخواست در هر عملیات) قرار می‌دهند.

برای نوشتن در کلیپ‌بورد، مشخصات فنی انتظار دارد که صفحه مجوز `clipboard-write` از [Permissions API](/en-US/docs/Web/API/Permissions_API) را دریافت کرده باشد، و مرورگر ممکن است به [فعال‌سازی موقت کاربر (transient user activation)](/en-US/docs/Web/Security/Defenses/User_activation) نیز نیاز داشته باشد. مرورگرها ممکن است محدودیت‌های اضافی برای استفاده از متدهای دسترسی به کلیپ‌بورد اعمال کنند.

رویداد {{domxref("Clipboard.clipboardchange_event", "clipboardchange")}} تنها با [فعال‌سازی چسبنده (sticky activation)](/en-US/docs/Glossary/Sticky_activation) یا پس از اعطای مجوز `clipboard-read` فعال می‌شود.

پیاده‌سازی‌های مرورگرها از مشخصات فنی فاصله گرفته‌اند. تفاوت‌ها در بخش [سازگاری مرورگر](#browser_compatibility) ثبت شده است و وضعیت فعلی در زیر خلاصه شده است:

مرورگرهای کروم (Chromium):

- اگر خواندن طبق مشخصات مجاز نباشد و سند فوکوس داشته باشد، درخواستی برای استفاده از مجوز `clipboard-read` ایجاد می‌کند و در صورت اعطای مجوز (چه به دلیل پذیرش درخواست توسط کاربر یا قبلاً اعطا شده باشد) موفق می‌شود.
- نوشتن نیاز به مجوز `clipboard-write` یا فعال‌سازی موقت دارد. اگر مجوز اعطا شود، پایدار می‌ماند و فعال‌سازی موقت بیشتری لازم نیست.
- مجوزهای HTTP [Permissions-Policy](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy) یعنی `clipboard-read` و `clipboard-write` باید برای عناصر {{HTMLElement("iframe")}} که به کلیپ‌بورد دسترسی دارند، مجاز باشند.

فایرفاکس و سافاری:

- اگر خواندن طبق مشخصات مجاز نباشد اما فعال‌سازی موقت کاربر همچنان برقرار باشد، یک اعلان کاربر به صورت یک منوی زمینه موقت با یک گزینه «چسباندن» (که پس از ۱ ثانیه فعال می‌شود) ایجاد می‌کند و در صورت انتخاب گزینه توسط کاربر موفق می‌شود.
- نوشتن نیاز به فعال‌سازی موقت دارد.
- اعلان چسباندن در صورت خواندن محتوای کلیپ‌بورد هم‌ریشه (same-origin) سرکوب می‌شود، اما برای محتوای غیر هم‌ریشه (cross-origin) نه.
- مجوزهای `clipboard-read` و `clipboard-write` توسط فایرفاکس یا سافاری پشتیبانی نمی‌شوند (و برنامه‌ای برای پشتیبانی ندارند).

افزونه‌های وب فایرفاکس:

- خواندن برای افزونه‌هایی که مجوز [`clipboardRead`](/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/permissions#clipboardread) را دارند در دسترس است. با این مجوز، افزونه نیازی به فعال‌سازی موقت یا استفاده از اعلان چسباندن ندارد. از فایرفاکس ۱۴۷، خواندن بدون مجوز نیز در یک زمینه امن، با فعال‌سازی موقت و پس از کلیک کاربر روی اعلان چسباندن در یک منوی زمینه موقت در دسترس است.
- نوشتن در یک زمینه امن و با فعال‌سازی موقت در دسترس است. با این حال، با مجوز [`clipboardWrite`](/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/permissions#clipboardwrite) فعال‌سازی موقت لازم نیست.

## مثال‌ها

### دسترسی به کلیپ‌بورد

کلیپ‌بورد سیستم از طریق شیء سراسری {{domxref("Navigator.clipboard")}} قابل دسترسی است.

این قطعه کد متن را از کلیپ‌بورد دریافت کرده و به اولین عنصر با کلاس `editor` اضافه می‌کند. از آنجایی که در صورت متنی نبودن کلیپ‌بورد، {{domxref("Clipboard.readText", "readText()")}} یک رشته خالی برمی‌گرداند، این کد ایمن است.

```js
navigator.clipboard
  .readText()
  .then(
    (clipText) => (document.querySelector(".editor").innerText += clipText),
  );
```

## مشخصات فنی

{{Specifications}}

## سازگاری مرورگر

{{Compat}}