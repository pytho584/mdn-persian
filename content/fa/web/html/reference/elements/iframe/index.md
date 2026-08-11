---
title: "<iframe> HTML inline frame element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/iframe"
translated_by: "n8n + AI"
---

عنصر **`<iframe>`** یک [HTML](/en-US/docs/Web/HTML) است که یک **browsing context** (زمینه مرور) تودرتو را نمایش می‌دهد؛ یعنی یک صفحهٔ HTML دیگر را درون صفحهٔ جاری جاسازی می‌کند.

```html interactive-example
<iframe
  id="inlineFrameExample"
  title="Inline Frame Example"
  width="300"
  height="200"
  src="https://www.openstreetmap.org/export/embed.html?bbox=-0.004017949104309083%2C51.47612752641776%2C0.00030577182769775396%2C51.478569861898606&amp;layer=mapnik">
</iframe>
```

```css interactive-example
iframe {
  border: 1px solid black;
  width: 100%; /* takes precedence over the width set with the HTML width attribute */
}
```

هر browsing context جاسازی‌شده، [document](/en-US/docs/Web/API/Document) مخصوص خود را دارد و می‌تواند URLها را باز کند. مسیریابی (navigation) هر یک از این contextها در [تاریخچه جلسه (session history)](/en-US/docs/Web/API/History) *بالاترین* browsing context به‌صورت خطی ذخیره می‌شود. به browsing contextای که دیگران را جاسازی می‌کند، *parent browsing context* (زمینه مرور والد) می‌گویند. *بالاترین* browsing context – همانی که والد ندارد – معمولاً پنجرهٔ مرورگر است که با شیء {{domxref("Window")}} نمایش داده می‌شود.

> [!WARNING]
> از آنجا که هر browsing context یک محیط document کامل است، هر `<iframe>` در یک صفحه حافظه و منابع محاسباتی بیشتری مصرف می‌کند. اگرچه از نظر تئوری می‌توانید به هر تعداد که دوست دارید `<iframe>` به کار ببرید، اما حتماً مشکلات عملکردی را بررسی کنید.

## ویژگی‌ها (Attributes)

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) نیز می‌شود.

- `allow`
  - : یک [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) (سیاست مجوزها) برای `<iframe>` مشخص می‌کند. این خط‌مشی تعیین می‌کند که بر اساس مبدأ درخواست، چه قابلیت‌هایی (مثلاً دسترسی به میکروفون، دوربین، باتری، web-share و غیره) در اختیار `<iframe>` قرار گیرد.

    برای مثال‌های بیشتر به بخش [iframes](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy#iframes) در مبحث `Permissions-Policy` مراجعه کنید.

    > [!NOTE]
    > Permissions Policyای که با ویژگی `allow` تعیین می‌شود، یک محدودیت اضافی بر روی خط‌مشی تعیین‌شده در هدر {{httpheader("Permissions-Policy")}} اعمال می‌کند و جایگزین آن نیست.

- `allowfullscreen`
  - : اگر `<iframe>` بتواند با فراخوانی متد {{domxref("Element.requestFullscreen", "requestFullscreen()")}} حالت تمام‌صفحه را فعال کند، مقدار `true` بدهید.

    > [!NOTE]
    > این ویژگی قدیمی در نظر گرفته می‌شود و با `allow="fullscreen *"` بازتعریف شده است.

- `allowpaymentrequest` {{deprecated_inline}} {{non-standard_inline}}
  - : اگر `<iframe>` چندمبدأیی (cross-origin) باید مجوز استفاده از [Payment Request API](/en-US/docs/Web/API/Payment_Request_API) را داشته باشد، مقدار `true` بدهید.

    > [!NOTE]
    > این ویژگی قدیمی در نظر گرفته می‌شود و با `allow="payment *"` بازتعریف شده است.

- `browsingtopics` {{non-standard_inline}} {{deprecated_inline}}
  - : یک ویژگی بولی (Boolean). اگر وجود داشته باشد، مشخص می‌کند که موضوعات (topics) انتخاب‌شده برای کاربر جاری باید همراه با درخواست منبع `<iframe>` ارسال شود.

- `credentialless` {{Experimental_Inline}}
  - : با `true` تنظیم کنید تا `<iframe>` بدون اعتبار (credentialless) شود. یعنی محتوای آن در یک context موقت و جدید بارگذاری می‌شود. این context به شبکه، کوکی‌ها و داده‌های ذخیره‌شده مرتبط با مبدأ خود دسترسی ندارد. در عوض از یک context جدید استفاده می‌کند که تا طول عمر document سطح بالا (top-level document) معتبر است. در مقابل، قوانین جاسازی {{httpheader("Cross-Origin-Embedder-Policy")}} (COEP) برداشته می‌شود، بنابراین documentهایی که COEP فعال دارند می‌توانند documentهای شخص ثالثی را که COEP ندارند جاسازی کنند. برای جزئیات بیشتر به [IFrame credentialless](/en-US/docs/Web/HTTP/Guides/IFrame_credentialless) مراجعه کنید.

- `csp`
  - : یک [Content Security Policy](/en-US/docs/Web/HTTP/Guides/CSP) که برای منبع جاسازیشده اعمال میشود. برای جزئیات، `HTMLIFrameElement.csp` را ببینید.

- `height`
  - : ارتفاع فریم بر حسب پیکسل‌های CSS. مقدار پیش‌فرض `150` است.

- `loading`
  - : نشان می‌دهد چه زمانی مرورگر باید iframe را بارگذاری کند:
    - `eager`
      - : بارگذاری iframe بلافاصله هنگام بارگذاری صفحه (این مقدار پیش‌فرض است).
    - `lazy`
      - : بارگذاری iframe را به تأخیر می‌اندازد تا زمانی که به فاصله محاسبه‌شده‌ای از visual viewport برسد، طبق تعریف مرورگر. هدف این است که از مصرف پهنای باند شبکه و فضای ذخیره‌سازی لازم برای دریافت فریم، تا زمانی که مرورگر نسبتاً مطمئن شود به آن نیاز دارد، جلوگیری شود. این کار در بیشتر موارد استفاده معمول، عملکرد و هزینه را بهبود می‌بخشد، به‌ویژه با کاهش زمان بارگذاری اولیه صفحه.

        بارگذاری فقط زمانی به تأخیر می‌افتد که JavaScript فعال باشد. این یک اقدام ضد ردیابی است؛ زیرا اگر یک user agent از بارگذاری تأخیری هنگام غیرفعال بودن اسکریپت پشتیبانی کند، باز هم ممکن است یک سایت موقعیت تقریبی اسکرول کاربر را در طول یک نشست ردگیری کند، با قرار دادن استراتژیک iframeها در مارکاپ صفحه به طوری که سرور بتواند تعداد iframeهای درخواست‌شده و زمان آن‌ها را ردگیری کند.

- `name`
  - : یک نام قابل هدف‌گیری برای زمینه مرور جاسازیشده. می‌توان از آن در attribute ی `target` در عناصر `a`، `form`، یا `base` استفاده کرد؛ همچنین در attribute ی `formtarget` در عناصر `input` یا `button`؛ یا پارامتر `windowName` در متد `window.open()`. علاوه بر این، نام به یک property از اشیاء `Window` و `Document` تبدیل می‌شود که ارجاعی به پنجره جاسازی‌شده یا خود عنصر را نگه می‌دارد.

- `privateToken`
  - : شامل یک نمایش رشته‌ای از یک آبجکت options است که یک عملیات [private state token](/en-US/docs/Web/API/Private_State_Token_API/Using) را نشان می‌دهد. این آبجکت ساختار مشابهی با property ی `privateToken` در دیکشنری `RequestInit` دارد. iframeهای دارای این attribute می‌توانند هنگام بارگذاری محتوای جاسازی‌شده، عملیاتی مانند صدور یا بازخرید token را آغاز کنند.

- `referrerpolicy`
  - : مشخص میکند هنگام دریافت منبع فریم، کدام [referrer](/en-US/docs/Web/API/Document/referrer) ارسال شود:
    - `no-referrer`
      - : هدر Referer ارسال نخواهد شد.
    - `no-referrer-when-downgrade`
      - : هدر Referer به originهایی که TLS (HTTPS) ندارند ارسال نخواهد شد.
    - `origin`
      - : referrer ارسالی به origin صفحهٔ ارجاعدهنده محدود میشود: شامل [scheme](/en-US/docs/Learn_web_development/Howto/Web_mechanics/What_is_a_URL)، host و port آن.
    - `origin-when-cross-origin`
      - : referrer ارسالی به سایر originها به scheme، host و port محدود میشود. در ناوبریهای same-origin همچنان path ارسال میشود.
    - `same-origin`
      - : برای درخواستهای same-origin یک referrer ارسال میشود، اما درخواستهای cross-origin هیچ اطلاعات referrer ندارند.
    - `strict-origin`
      - : فقط زمانی که سطح امنیت پروتکل یکسان باشد (HTTPS→HTTPS)، origin سند را بهعنوان referrer ارسال کن؛ اما به مقصد کماستان (HTTPS→HTTP) ارسال نکن.
    - `strict-origin-when-cross-origin` (پیشفرض)
      - : برای درخواست same-origin، URL کامل ارسال شود؛ وقتی سطح امنیت پروتکل یکسان است (HTTPS→HTTPS) فقط origin ارسال شود؛ و به مقصد کماستان (HTTPS→HTTP) هیچ هدری ارسال نشود.
    - `unsafe-url`
      - : referrer شامل origin _و_ path خواهد بود (اما شامل [fragment](/en-US/docs/Web/API/HTMLAnchorElement/hash)، [password](/en-US/docs/Web/API/HTMLAnchorElement/password) یا [username](/en-US/docs/Web/API/HTMLAnchorElement/username) نیست). **این مقدار unsafe است**، چون originها و pathها را از منابع محافظتشده با TLS به originهای ناامن نشت میدهد.

```markdown
- `sandbox`
  - : کنترل می‌کند که چه محدودیت‌هایی روی محتوای تعبیه‌شده در `<iframe>` اعمال شود. مقدار این attribute می‌تواند خالی باشد تا همهٔ محدودیت‌ها اعمال شوند، یا شامل توکن‌هایی باشد که با فاصله از هم جدا شده‌اند تا محدودیت‌های خاصی برداشته شوند:
    - `allow-downloads`
      - : اجازه می‌دهد فایل‌ها از طریق یک عنصر `<a>` یا `<area>` با attribute `download` دانلود شوند؛ همچنین از طریق navigation که به دانلود فایل منجر می‌شود. این صرف‌نظر از اینکه کاربر روی لینک کلیک کرده باشد یا کد JS بدون تعامل کاربر آن را آغاز کرده باشد، کار می‌کند.
    - `allow-forms`
      - : اجازه می‌دهد صفحه فرم‌ها را ارسال کند. اگر این کلیدواژه استفاده نشود، فرم به صورت عادی نمایش داده می‌شود، اما ارسال آن اعتبارسنجی ورودی را فعال نمی‌کند، داده‌ای به سرور وب نمی‌فرستد، یا دیالوگی را نمی‌بندد.
    - `allow-modals`
      - : اجازه می‌دهد صفحه پنجره‌های modal را با `Window.alert()`، `Window.confirm()`، `Window.print()` و `Window.prompt()` باز کند. باز کردن یک `<dialog>` بدون توجه به این کلیدواژه مجاز است. همچنین به صفحه اجازه می‌دهد رویداد `BeforeUnloadEvent` را دریافت کند.
    - `allow-orientation-lock`
      - : به منبع اجازه می‌دهد جهت صفحه‌نمایش را قفل کند ([lock the screen orientation](/en-US/docs/Web/API/Screen/lockOrientation)).
    - `allow-pointer-lock`
      - : به صفحه اجازه می‌دهد از [Pointer Lock API](/en-US/docs/Web/API/Pointer_Lock_API) استفاده کند.
    - `allow-popups`
      - : اجازه می‌دهد popup ها (مثلاً ساخته‌شده با `Window.open()` یا `target="_blank"`) نمایش داده شوند. اگر این کلیدواژه استفاده نشود، چنین قابلیتی بی‌صدا با شکست مواجه می‌شود.
    - `allow-popups-to-escape-sandbox`
      - : به یک سند sandbox شده اجازه می‌دهد یک browsing context جدید را بدون تحمیل پرچم‌های sandbox به آن باز کند. این امکان، برای مثال، به یک تبلیغ شخص ثالث اجازه می‌دهد که به طور امن sandbox شود بدون اینکه همان محدودیت‌ها بر صفحه‌ای که آگهی به آن لینک می‌دهد اعمال شود. اگر این پرچم در نظر گرفته نشود، یک صفحهٔ هدایت‌شده، پنجرهٔ popup یا تب جدید مشمول همان محدودیت‌های sandbox ایفری مبدأ خواهد بود.
    - `allow-presentation`
      - : به تعبیه‌کنندگان اجازه می‌دهد کنترل کنند که آیا یک iframe می‌تواند یک جلسهٔ نمایش ([presentation session](/en-US/docs/Web/API/PresentationRequest)) را شروع کند یا نه.
    - `allow-same-origin`
      - : اگر این توکن استفاده نشود، منبع به عنوان یک origin خاص در نظر گرفته می‌شود که همیشه در same-origin policy شکست می‌خورد (و احتمالاً دسترسی به [data storage/cookies](/en-US/docs/Web/Security/Defenses/Same-origin_policy#cross-origin_data_storage_access) و برخی APIهای جاوااسکریپت را مسدود می‌کند).
        > [!NOTE]
        > وقتی `allow-same-origin` حضور داشته باشد، یک سند والد با همان origin همچنان می‌تواند به DOM ایفری دسترسی داشته باشد و با آن تعامل کند، حتی اگر `allow-scripts` تنظیم نشده باشد. توکن `allow-scripts` فقط اجرای اسکریپت را در browsing context تعبیه‌شده کنترل می‌کند و بر دسترسی DOM از سمت والد تأثیری ندارد.
    - `allow-scripts`
      - : به صفحه اجازه می‌دهد اسکریپت‌ها را اجرا کند (اما پنجره‌های popup ایجاد نکند). اگر این کلیدواژه استفاده نشود، این عملیات مجاز نیست.
    - `allow-storage-access-by-user-activation` (آزمایشی)
      - : به سندی که در `<iframe>` بارگذاری شده اجازه می‌دهد از [Storage Access API](/en-US/docs/Web/API/Storage_Access_API) برای درخواست دسترسی به کوکی‌های unpartitioned استفاده کند.
    - `allow-top-navigation`
      - : به منبع اجازه می‌دهد در browsing context سطح بالا (که `_top` نام دارد) ناوبری کند.
    - `allow-top-navigation-by-user-activation`
      - : به منبع اجازه می‌دهد در browsing context سطح بالا ناوبری کند، اما فقط اگر توسط یک gesture کاربر آغاز شده باشد.
    - `allow-top-navigation-to-custom-protocols`
      - : اجازه می‌دهد به پروتکل‌های غیر از `http` که در مرورگر تعبیه شده‌اند یا [توسط یک وب‌سایت ثبت شده‌اند](/en-US/docs/Web/API/Navigator/registerProtocolHandler) ناوبری صورت گیرد. این قابلیت همچنین توسط کلیدواژه‌های `allow-popups` یا `allow-top-navigation` فعال می‌شود.
```

> [!NOTE]
> - زمانی که سند تعبیه‌شده با صفحهٔ میزبان دارای `origin` یکسان است، **اکیداً توصیه نمی‌شود** که هم از `allow-scripts` و هم از `allow-same-origin` استفاده کنید، زیرا این کار به سند تعبیه‌شده اجازه می‌دهد ویژگی `sandbox` را حذف کند — در نتیجه امنیت آن از حالتی که اصلاً از `sandbox` استفاده نشده باشد بیشتر نخواهد بود.
> - اگر مهاجم بتواند محتوا را خارج از یک `iframe` sandbox شده نمایش دهد (مثلاً کاربر فریم را در تب جدید باز کند)، sandboxing بی‌فایده است. چنین محتوایی باید از یک `origin` جداگانه (separate origin) ارائه شود تا آسیب احتمالی محدود شود.

> [!NOTE]
> هنگام هدایت کاربر، باز کردن پنجره popup یا باز کردن تب جدید از یک صفحهٔ تعبیه‌شده درون `<iframe>` با ویژگی `sandbox`، بافت مرورگر جدید (new browsing context) مشمول همان محدودیت‌های `sandbox` خواهد بود. این می‌تواند مشکلاتی ایجاد کند — مثلاً اگر صفحه‌ای که درون `<iframe>` بدون ویژگی‌های `sandbox="allow-forms"` یا `sandbox="allow-popups-to-escape-sandbox"` تعبیه شده، یک سایت جدید را در تب جداگانه باز کند، ارسال فرم در آن بافت مرورگر جدید بی‌صدا (silently) شکست می‌خورد.

- `src`
  - : URL صفحه‌ای که قرار است تعبیه شود. از مقدار `about:blank` برای تعبیه یک صفحه خالی استفاده کنید که با [same-origin policy](/en-US/docs/Web/Security/Defenses/Same-origin_policy#inherited_origins) (مبدأهای به‌ارث‌برده) مطابقت دارد. همچنین توجه داشته باشید که حذف برنامه‌ای (programmatically) ویژگی `src` یک `<iframe>` (مثلاً از طریق {{domxref("Element.removeAttribute()")}}) باعث می‌شود `about:blank` در فریم بارگذاری شود. این رفتار در Firefox (از نسخه ۶۵)، مرورگرهای مبتنی بر Chromium و Safari/iOS دیده می‌شود.

    > [!NOTE]
    > صفحهٔ `about:blank` از URL سند میزبان به عنوان base URL خود برای حل URLهای نسبی (مانند لینک‌های لنگر) استفاده می‌کند.

- `srcdoc`
  - : HTML درون‌خطی (inline) برای تعبیه که ویژگی `src` را بازنویسی می‌کند. محتوای آن باید از نحو (syntax) یک سند کامل HTML پیروی کند که شامل دستور doctype، تگ‌های `<html>`، `<body>` و غیره است، اگرچه بسیاری از آن‌ها قابل حذف هستند و فقط محتوای بدنه باقی می‌ماند. این سند مکان (location) خود را `about:srcdoc` خواهد داشت. اگر مرورگر از ویژگی `srcdoc` پشتیبانی نکند، به URL موجود در ویژگی `src` بازمی‌گردد (fall back).

    > [!NOTE]
    > صفحهٔ `about:srcdoc` از URL سند میزبان به عنوان base URL خود برای حل URLهای نسبی (مانند لینک‌های لنگر) استفاده می‌کند.

- `width`
  - : عرض فریم بر حسب پیکسل CSS. مقدار پیش‌فرض `300` است.

### ویژگی‌های منسوخ‌شده (Deprecated attributes)

این ویژگی‌ها منسوخ شده‌اند و ممکن است دیگر توسط همهٔ عامل‌های کاربر (user agents) پشتیبانی نشوند. نباید از آن‌ها در محتوای جدید استفاده کنید و سعی کنید آن‌ها را از محتوای موجود حذف کنید.

- `align` {{deprecated_inline}}
  - : ترازبندی این عنصر نسبت به زمینه (context) اطراف.
- `frameborder` {{deprecated_inline}}
  - : مقدار `1` (پیش‌فرض) یک حاشیه دور این فریم رسم می‌کند. مقدار `0` حاشیه را حذف می‌کند، اما بهتر است از ویژگی CSS {{cssxref("border")}} برای کنترل حاشیه‌های `<iframe>` استفاده کنید.
- `longdesc` {{deprecated_inline}}
  - : URL یک توضیح طولانی از محتوای فریم. به دلیل استفاده نادرست گسترده، این برای مرورگرهای غیربصری مفید نیست.
- `marginheight` {{deprecated_inline}}
  - : مقدار فاصله بر حسب پیکسل بین محتوای فریم و حاشیه‌های بالا و پایین آن.
- `marginwidth` {{deprecated_inline}}
  - : مقدار فاصله بر حسب پیکسل بین محتوای فریم و حاشیه‌های چپ و راست آن.
- `scrolling` {{deprecated_inline}}
  - : نشان می‌دهد که مرورگر چه زمانی باید نوار اسکرول برای فریم فراهم کند:
    - `auto`
      - : فقط زمانی که محتوای فریم بزرگ‌تر از ابعاد آن باشد.
    - `yes`
      - : همیشه نوار اسکرول را نشان دهد.
    - `no`
      - : هرگز نوار اسکرول را نشان ندهد.

## Scripting

فریم‌های درون‌خطی (inline frames)، مانند عناصر {{HTMLElement("frame")}}، در آرایه شبه (pseudo-array) {{domxref("window.frames")}} قرار می‌گیرند.

با استفاده از شیء DOM به نام `HTMLIFrameElement`، اسکریپت‌ها می‌توانند از طریق خاصیت `contentWindow` به شیء `window` صفحهٔ درون iframe دسترسی داشته باشند. خاصیت `contentDocument` به `document` داخل `<iframe>` اشاره می‌کند، همانند `contentWindow.document`.

از داخل یک فریم، اسکریپت می‌تواند با استفاده از `window.parent` به پنجرهٔ والد دسترسی پیدا کند.

دسترسی اسکریپت به محتوای یک فریم تابع [سیاست same-origin](/en-US/docs/Web/Security/Defenses/Same-origin_policy) است. اسکریپت‌ها نمی‌توانند به بیشتر خاصیت‌های اشیاء `window` دیگر دسترسی داشته باشند اگر اسکریپت از یک origin متفاوت بارگذاری شده باشد، از جمله اسکریپت‌های داخل یک فریم که به والد فریم دسترسی پیدا می‌کنند. ارتباط cross-origin را می‌توان با استفاده از `Window.postMessage()` انجام داد.

### پیمایش به بالا (top navigation) در فریم‌های cross-origin

اسکریپت‌هایی که در یک فریم same-origin اجرا می‌شوند می‌توانند به خاصیت `Window.top` دسترسی داشته باشند و با تنظیم `window.top.location` صفحهٔ سطح بالا را به یک مکان جدید هدایت کنند. این رفتار «پیمایش به بالا» (top navigation) نامیده می‌شود.

یک فریم cross-origin تنها در صورتی مجاز است که با استفاده از `top` صفحهٔ سطح بالا را هدایت کند که فریم دارای [sticky activation](https://developer.mozilla.org/en-US/docs/Glossary/Sticky_activation) باشد. اگر پیمایش به بالا مسدود شود، مرورگرها ممکن است از کاربر اجازهٔ هدایت بگیرند یا خطا را در کنسول توسعه‌دهنده گزارش دهند (یا هر دو). این محدودیت توسط مرورگرها _framebusting intervention_ نامیده می‌شود. یعنی یک فریم cross-origin نمی‌تواند بلافاصله صفحهٔ سطح بالا را هدایت کند — کاربر باید قبلاً با فریم تعامل داشته باشد یا اجازهٔ هدایت را داده باشد.

یک فریم sandboxed تمام پیمایش‌های به بالا را مسدود می‌کند مگر اینکه مقادیر ویژگی `sandbox` روی [`allow-top-navigation`](#allow-top-navigation) یا [`allow-top-navigation-by-user-activation`](#allow-top-navigation-by-user-activation) تنظیم شده باشند. توجه داشته باشید که مجوزهای پیمایش به بالا به ارث می‌رسند، بنابراین یک فریم تو در تو فقط در صورتی می‌تواند پیمایش به بالا انجام دهد که فریم‌های والد آن نیز مجاز باشند.

## موقعیت‌یابی و مقیاس‌بندی

به عنوان یک [replaced element](https://developer.mozilla.org/en-US/docs/Glossary/Replaced_elements)، `<iframe>` امکان تنظیم موقعیت سند جاسازی‌شده درون جعبهٔ خود را با استفاده از خاصیت CSS `object-position` فراهم می‌کند.

> [!NOTE]
> خاصیت CSS `object-fit` روی عناصر `<iframe>` اثری ندارد.

## رفتار رویدادهای `error` و `load`

رویدادهای `error` و `load` که روی `<iframe>`ها رخ می‌دهند می‌توانند برای کاوش فضای URL سرورهای HTTP شبکهٔ محلی استفاده شوند. بنابراین، به عنوان یک اقدام امنیتی، user agentها رویداد [error](/en-US/docs/Web/API/HTMLElement/error_event) را روی `<iframe>`ها فعال نمی‌کنند، و رویداد [load](/en-US/docs/Web/API/HTMLElement/load_event) همیشه حتی اگر محتوای `<iframe>` بارگذاری نشود، فعال می‌شود.

## اندازه‌گذاری پاسخگو (responsive) `<iframe>`

به دلایل امنیتی و حریم خصوصی، عناصر `<iframe>` به طور پیش‌فرض هیچ اطلاعاتی دربارهٔ اندازهٔ محتوای سند جاسازی‌شده به سند والد ارائه نمی‌دهند.

برای فعال کردن اندازه‌گذاری پاسخگوی عناصر `<iframe>` بر اساس محتوایشان، می‌توان تگ `<meta name="responsive-embedded-sizing">` را در سند جاسازی‌شده قرار داد تا آن را برای اشتراک‌گذاری اطلاعات اندازه با سند والد انتخاب کند. سپس خاصیت CSS `frame-sizing` را می‌توان روی `<iframe>` تنظیم کرد تا همان اندازهٔ افقی یا عمودی اندازهٔ واقعی محتوای سند جاسازی‌شده را بگیرد. این کار تضمین می‌کند که محتوای `<iframe>` به طور یکپارچه در درون‌گیرنده (embedder) خود قرار می‌گیرد و از اسکرول‌بارهای غیرضروری جلوگیری می‌کند.

برای تغییر اندازهٔ `<iframe>` به صورت پویا با تغییر اندازهٔ layout سند جاسازی‌شده، می‌توانید متد `Window.requestResize()` را از سند جاسازی‌شده فراخوانی کنید تا اندازهٔ به‌روز شده را گزارش دهد.

## دسترسی‌پذیری

افرادی که با فناوری‌های کمکی مانند صفحه‌خوان‌ها از وب استفاده می‌کنند، می‌توانند برای برچسب‌گذاری محتوای یک `<iframe>` از ویژگی `title` روی آن استفاده کنند. مقدار این `title` باید محتوای جاسازی‌شده را به‌طور مختصر توصیف کند:

```html
<iframe
  title="Wikipedia page for Avocados"
  src="https://en.wikipedia.org/wiki/Avocado"></iframe>
```

بدون این `title`، آن‌ها مجبور می‌شوند برای فهمیدن محتوای جاسازی‌شده، وارد `<iframe>` شوند. این تغییر بافت (context) می‌تواند گیج‌کننده و زمان‌بر باشد، به‌ویژه در صفحه‌هایی که چند `<iframe>` دارند یا محتوای تعاملی مثل ویدیو یا صدا داخل آن‌ها جاسازی شده است.

## مثال‌ها

### یک `<iframe>` ساده

این مثال، صفحهٔ <https://example.org> را درون یک `iframe` جاسازی می‌کند. این یک کاربرد رایج iframe است: جاسازی محتوا از یک سایت دیگر. برای مثال، خود نمونهٔ زنده و مثال [«try it»](#try_it) در بالای صفحه، هر دو `<iframe>`هایی هستند که محتوایی از یک سایت دیگر MDN را جاسازی کرده‌اند.

#### HTML

```html
<iframe
  src="https://example.org"
  title="iframe Example 1"
  width="400"
  height="300">
</iframe>
```

#### نتیجه

### جاسازی کد منبع درون یک `<iframe>`

این مثال، کد منبع را مستقیماً درون یک `iframe` رندر می‌کند. این روش می‌تواند به‌عنوان تکنیکی برای جلوگیری از تزریق اسکریپت هنگام نمایش محتوای تولیدشده توسط کاربر، در ترکیب با ویژگی `sandbox` استفاده شود.

توجه داشته باشید که هنگام استفاده از `srcdoc`، هر URL نسبی در محتوای جاسازی‌شده، نسبت به URL صفحهٔ میزبان (embedding page) تفسیر می‌شود. اگر می‌خواهید از پیوندهای درون‌صفحه‌ای (anchor links) برای اشاره به بخش‌هایی از محتوای جاسازی‌شده استفاده کنید، باید به‌صراحت `about:srcdoc` را به‌عنوان URL پایه مشخص کنید.

#### HTML

```html-nolint
<article>
  <footer>Nine minutes ago, <i>jc</i> wrote:</footer>
  <iframe
    sandbox
    srcdoc="<p>There are two ways to use the <code>iframe</code> element:</p>
<ol>
<li><a href=&quot;about:srcdoc#embed_another&quot;>To embed content from another page</a></li>
<li><a href=&quot;about:srcdoc#embed_user&quot;>To embed user-generated content</a></li>
</ol>
<h2 id=&quot;embed_another&quot;>Embedding content from another page</h2>
<p>Use the <code>src</code> attribute to specify the URL of the page to embed:</p>
<pre><code>&amp;lt;iframe src=&quot;https://example.org&quot;&amp;gt;&amp;lt;/iframe&amp;gt;</code></pre>
<h2 id=&quot;embed_user&quot;>Embedding user-generated content</h2>
<p>Use the <code>srcdoc</code> attribute to specify the content to embed. This post is already an example!</p>
"
    width="500"
    height="250"
></iframe>
</article>
```

در ادامه، روش نوشتن escape sequence ها هنگام استفاده از `srcdoc` آمده است:

- ابتدا HTML را بنویسید و هر کاراکتری را که در یک سند HTML معمولی escape می‌کنید (مانند `<`، `>`، `&` و...) escape کنید.
- `&lt;` و `<` در ویژگی `srcdoc` دقیقاً کاراکتر یکسانی را نشان می‌دهند. بنابراین، برای اینکه این مقدار به یک escape sequence واقعی در سند HTML تبدیل شود، هر علامت `&` را با `&amp;` جایگزین کنید. مثلاً `&lt;` به `&amp;lt;` و `&amp;` به `&amp;amp;` تبدیل می‌شود.
- برای جلوگیری از پایان زودهنگام ویژگی `srcdoc`، هر علامت نقل‌قول دوتایی (`"`) را با `&quot;` جایگزین کنید (اگر به جای آن از `'` استفاده می‌کنید، باید `'` را با `&apos;` عوض کنید). این مرحله بعد از مرحلهٔ قبل انجام می‌شود، بنابراین `&quot;` که در این مرحله تولید می‌شود به `&amp;quot;` تبدیل نمی‌شود.

#### نتیجه

| ویژگی | مقدار |
| --- | --- |
| دسته‌بندی محتوا | شامل [Flow content](</en-US/docs/Web/HTML/Guides/Content_categories#flow_content>)، [phrasing content](</en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content>)، embedded content، interactive content و palpable content. |
| محتوای مجاز | هیچ. |
| حذف تگ | هیچ؛ هم تگ آغاز و هم تگ پایان اجباری هستند. |
| والدین مجاز | هر عنصری که محتوای تعبیه‌شده (embedded content) را بپذیرد. |
| نقش ضمنی ARIA | [No corresponding role](https://w3c.github.io/html-aria/#dfn-no-corresponding-role) |
| نقش‌های ARIA مجاز | شامل [application](</en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role>)، [document](</en-US/docs/Web/Accessibility/ARIA/Reference/Roles/document_role>)، [img](</en-US/docs/Web/Accessibility/ARIA/Reference/Roles/img_role>)، [none](</en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role>) و [presentation](</en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role>) |
| رابط DOM | `HTMLIFrameElement` |

## همچنین ببینید

- [CSP: frame-ancestors](</en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/frame-ancestors>)
- [Privacy, permissions, and information security](</en-US/docs/Web/Privacy>)
- [Local network access](</en-US/docs/Web/Security/Defenses/Local_network_access>)