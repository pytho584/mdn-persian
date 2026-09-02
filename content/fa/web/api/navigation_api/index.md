---
title: Navigation API
slug: Web/API/Navigation_API
page-type: web-api-overview
browser-compat:
  - api.Navigation
  - api.NavigationDestination
  - api.NavigationHistoryEntry
  - api.NavigationTransition
spec-urls: https://html.spec.whatwg.org/multipage/nav-history-apis.html#navigation-api
---

{{DefaultAPISidebar("Navigation API")}}

**Navigation API** توانایی شروع، رهگیری و مدیریت کنش‌های ناوبری مرورگر را فراهم می‌کند و همچنین می‌تواند ورودی‌های تاریخچه یک برنامه را بررسی کند. این API جانشینی برای قابلیت‌های پیشین پلتفرم وب مانند {{domxref("History API", "", "", "nocode")}} و {{domxref("window.location")}} است که کاستی‌های آن‌ها را برطرف می‌کند و به‌طور خاص برای نیازهای {{glossary("SPA", "single-page applications (SPAs)")}} طراحی شده است.

## مفاهیم و کاربرد

در برنامه‌های تک‌صفحه‌ای، قالب صفحه معمولاً در طول استفاده ثابت می‌ماند و محتوا با مراجعه کاربر به صفحات یا ویژگی‌های مختلف به‌صورت پویا بازنویسی می‌شود. در نتیجه، تنها یک صفحه مشخص در مرورگر بارگذاری می‌شود و این موضوع تجربه کاربری موردانتظارِ رفتن به جلو و عقب بین مکان‌های مختلف در تاریخچه مشاهده را مختل می‌کند. این مشکل تا حدی از طریق {{domxref("History API", "", "", "nocode")}} قابل‌حل است، اما آن API برای نیازهای SPA طراحی نشده است. Navigation API قصد دارد این شکاف را پر کند.

این API از طریق ویژگی {{domxref("Window.navigation")}} در دسترس قرار می‌گیرد که ارجاعی به یک شیء سراسری {{domxref("Navigation")}} برمی‌گرداند. هر شیء `window` نمونه `navigation` متناظر خودش را دارد.

### مدیریت ناوبری‌ها

رابط `navigation` چند رویداد مرتبط دارد که مهم‌ترین آن‌ها رویداد {{domxref("Navigation/navigate_event", "navigate")}} است. این رویداد زمانی فعال می‌شود که [هر نوع ناوبری](https://github.com/WICG/navigation-api#appendix-types-of-navigations) آغاز گردد؛ یعنی می‌توانید همه ناوبری‌های صفحه را از یک نقطه مرکزی کنترل کنید؛ ایدئال برای قابلیت مسیریابی در چارچوب‌های SPA. (در مورد {{domxref("History API", "", "", "nocode")}} چنین نیست؛ جایی که گاهی تشخیص و پاسخ به همه ناوبری‌ها دشوار است.) به مدیریت‌کننده رویداد `navigate` یک شیء {{domxref("NavigateEvent")}} ارسال می‌شود که حاوی اطلاعات دقیقی است؛ از جمله جزئیات مربوط به مقصد ناوبری، نوع آن، اینکه آیا داده‌های فرم `POST` یا درخواست دانلود دارد و موارد دیگر.

شیء `NavigateEvent` همچنین دو متد فراهم می‌کند:

- {{domxref("NavigateEvent.intercept", "intercept()")}} به شما امکان می‌دهد رفتار سفارشی برای ناوبری‌ها تعیین کنید و می‌تواند آرگومان‌های زیر را بگیرد:
  - توابع مدیریت‌کننده بازگشتی که به شما امکان می‌دهند مشخص کنید هم _زمانی که_ ناوبری ثبت (commit) می‌شود و هم _درست قبل از_ ثبت شدن آن چه اتفاقی بیفتد. برای مثال، می‌توانید محتوای جدید مرتبط را بر اساس مسیر URL مقصد در رابط کاربری بارگذاری کنید، یا اگر URL به صفحه‌ای محدودشده اشاره کند و کاربر وارد نشده باشد، مرورگر را به صفحه ورود هدایت کنید.
  - ویژگی‌هایی که به شما امکان می‌دهند رفتار پیش‌فرض مرورگر در مورد تمرکز و پیمایش را پس از انجام ناوبری فعال یا غیرفعال کنید.
- {{domxref("NavigateEvent.scroll", "scroll()")}} به شما امکان می‌دهد رفتار پیمایش مرورگر را به‌صورت دستی آغاز کنید (مثلاً پیمایش به یک شناسه قطعه در URL)، اگر برای کدتان منطقی است، به‌جای اینکه منتظر بمانید مرورگر آن را خودکار انجام دهد.

هنگامی که ناوبری آغاز می‌شود و مدیریت‌کننده `intercept()` شما فراخوانده می‌شود، یک نمونه از شیء {{domxref("NavigationTransition")}} ساخته می‌شود (از طریق {{domxref("Navigation.transition")}} قابل دسترسی است) که می‌توان از آن برای پیگیری روند ناوبری در حال انجام استفاده کرد.

> [!NOTE]
> در این زمینه، «transition» به تغییر بین دو ورودی تاریخچه اشاره دارد و ربطی به transitionهای CSS ندارد.

> [!NOTE]
> همچنین می‌توانید برای توقف کامل ناوبری در بیشتر [انواع ناوبری](/en-US/docs/Web/API/NavigateEvent/navigationType#value) متد {{domxref("Event.preventDefault", "preventDefault()")}} را فراخوانی کنید؛ لغو ناوبری‌های عبوری (traverse) هنوز پیاده‌سازی نشده است.

هنگامی که وعده‌های (promise) بازگشتی از توابع مدیریت‌کننده `intercept()` با موفقیت انجام شوند (fulfill)، رویداد {{domxref("Navigation/navigatesuccess_event", "navigatesuccess")}} شیء `Navigation` فعال می‌شود و به شما اجازه می‌دهد پس از تکمیل موفقیت‌آمیز ناوبری، کدهای پاک‌سازی را اجرا کنید. اگر این وعده‌ها رد شوند (reject) — به این معنی که ناوبری ناموفق بوده — در عوض رویداد {{domxref("Navigation/navigateerror_event", "navigateerror")}} فعال می‌شود تا بتوانید به‌شکلی مناسب حالت شکست را مدیریت کنید. همچنین یک ویژگی `finished` در مقدار بازگشتی متدهای ناوبری (مانند {{domxref("Navigation.navigate()")}}) وجود دارد که همزمان با فعال‌شدن رویدادهای یادشده با موفقیت انجام یا رد می‌شود و مسیر دیگری برای مدیریت حالت‌های موفقیت و شکست فراهم می‌کند.

> [!NOTE]
> پیش از در دسترس بودن Navigation API، برای انجام کاری مشابه باید به همه رویدادهای کلیک روی پیوندها گوش می‌دادید، `e.preventDefault()` را اجرا می‌کردید، فراخوانی مناسب {{domxref("History.pushState()")}} را انجام می‌دادید و سپس نمای صفحه را بر اساس URL جدید می‌ساختید. و این روش نیز همه ناوبری‌ها را پوشش نمی‌داد — فقط کلیک‌های آغازشده توسط کاربر روی پیوندها را مدیریت می‌کرد.

### به‌روزرسانی و پیمایش برنامه‌ای در تاریخچه ناوبری

همان‌طور که کاربر در برنامه شما ناوبری می‌کند، هر مکان جدیدی که به آن ناوبری شود منجر به ایجاد یک ورودی در تاریخچه ناوبری می‌شود. هر ورودی تاریخچه با یک نمونه شیء مجزای {{domxref("NavigationHistoryEntry")}} نمایش داده می‌شود. این نمونه‌ها چند ویژگی دارند؛ مانند کلید (key) ورودی، URL و اطلاعات state. می‌توانید ورودی‌ای که کاربر در حال حاضر روی آن است را با {{domxref("Navigation.currentEntry")}} و آرایه‌ای از همه ورودی‌های تاریخچه موجود را با {{domxref("Navigation.entries()")}} به دست آورید. هر شیء `NavigationHistoryEntry` یک رویداد {{domxref("NavigationHistoryEntry/dispose_event", "dispose")}} دارد که وقتی ورودی دیگر بخشی از تاریخچه مرورگر نباشد فعال می‌شود. مثلاً اگر کاربر سه بار به عقب برود و سپس به سمت جای دیگری به جلو برود، آن سه ورودی تاریخچه حذف (dispose) خواهند شد.

> [!NOTE]
> Navigation API فقط ورودی‌های تاریخچه‌ای را در معرض دید قرار می‌دهد که در بستر مرور فعلی (current browsing context) ایجاد شده‌اند و همریشه (same-origin) با صفحه فعلی هستند (مثلاً نه ناوبری‌های داخل {{htmlelement("iframe")}}های توکار و نه ناوبری‌های cross-origin). بنابراین فهرست دقیقی از همه ورودی‌های قبلی تاریخچه فقط برای برنامه شما فراهم می‌کند. این موضوع، پیمایش در تاریخچه را در مقایسه با {{domxref("History API", "", "", "nocode")}} قدیمی بسیار کم‌خطاتر می‌کند.

شیء `Navigation` شامل همه متدهایی است که برای به‌روزرسانی و پیمایش در تاریخچه ناوبری نیاز دارید:

- {{domxref("Navigation.navigate", "navigate()")}}
  - : به یک URL جدید ناوبری می‌کند و یک ورودی تاریخچه ناوبری جدید می‌سازد.
- {{domxref("Navigation.reload", "reload()")}}
  - : ورودی تاریخچه ناوبری فعلی را دوباره بارگذاری می‌کند.
- {{domxref("Navigation.back", "back()")}}
  - : در صورت امکان، به ورودی تاریخچه ناوبری قبلی می‌رود.
- {{domxref("Navigation.forward", "forward()")}}
  - : در صورت امکان، به ورودی تاریخچه ناوبری بعدی می‌رود.
- {{domxref("Navigation.traverseTo", "traverseTo()")}}
  - : به یک ورودی مشخص از تاریخچه ناوبری که با مقدار کلیدش شناسایی می‌شود، ناوبری می‌کند. این مقدار از طریق ویژگی {{domxref("NavigationHistoryEntry.key")}} ورودی مربوطه به دست می‌آید.

هر یک از متدهای بالا یک شیء شامل دو promise برمی‌گرداند — `{ committed, finished }`. این امکان را به تابع فراخوان فراهم می‌کند که برای انجام اقدام بعدی صبر کند تا:

- `committed` با موفقیت انجام شود؛ یعنی URL قابل مشاهده تغییر کرده و یک {{domxref("NavigationHistoryEntry")}} جدید ساخته شده است.
- `finished` با موفقیت انجام شود؛ یعنی همه promiseهای بازگشتی از مدیریت‌کننده `intercept()` شما fulfilled شده‌اند. این معادل fulfilled شدن وعده {{domxref("NavigationTransition.finished")}} است، هنگام‌یکه رویداد {{domxref("Navigation/navigatesuccess_event", "navigatesuccess")}} فعال می‌شود، همان‌طور که پیش‌تر اشاره شد.
- هر یک از دو promise بالا رد (reject) شود؛ یعنی ناوبری به دلایلی ناموفق بوده است.

### State

Navigation API به شما امکان می‌دهد state را روی هر ورودی تاریخچه ذخیره کنید. این اطلاعات توسط توسعه‌دهنده تعریف می‌شود و می‌تواند هر چیزی باشد که می‌خواهید. برای مثال، ممکن است بخواهید یک ویژگی `visitCount` ذخیره کنید که تعداد دفعات مشاهده شدن یک نما را ثبت کند، یا یک شیء حاوی چند ویژگی مرتبط با state رابط کاربری ذخیره کنید تا وقتی کاربر به آن نما بازگشت، state بازیابی شود.

برای دریافت state یک {{domxref("NavigationHistoryEntry")}}، متد {{domxref("NavigationHistoryEntry.getState", "getState()")}} آن را فراخوانی می‌کنید. این مقدار در ابتدا `undefined` است، اما وقتی اطلاعات state روی ورودی تنظیم شود، اطلاعات stateای که قبلاً تنظیم شده بود را برمی‌گرداند.

تنظیم state کمی ظریف‌تر است. نمی‌توانید مقدار state را بازیابی کنید و سپس آن را به‌طور مستقیم به‌روزرسانی کنید — کپی‌ای که روی ورودی ذخیره شده تغییر نخواهد کرد. در عوض، آن را هنگام انجام {{domxref("Navigation.navigate", "navigate()")}} یا {{domxref("Navigation.reload", "reload()")}} به‌روزرسانی می‌کنید؛ هر یک از این‌ها به‌صورت اختیاری یک پارامتر شیء options می‌پذیرند که شامل ویژگی `state` حاوی state جدید موردنظر برای تنظیم روی ورودی تاریخچه است. وقتی این ناوبری‌ها ثبت (commit) شوند، تغییر state به‌طور خودکار اعمال می‌شود.

با این حال، در برخی موارد تغییر state از ناوبری یا بارگذاری مجدد مستقل است؛ مثلاً وقتی صفحه حاوی یک عنصر {{htmlelement("details")}} بازشو/جمع‌شونده باشد. در این حالت، ممکن است بخواهید state باز یا بسته بودن را در ورودی تاریخچه ذخیره کنید تا وقتی کاربر به صفحه بازگشت یا مرورگر را دوباره راه‌اندازی کرد، آن را بازیابی کنید. چنین مواردی با {{domxref("Navigation.updateCurrentEntry()")}} مدیریت می‌شوند. رویداد {{domxref("Navigation/currententrychange_event", "currententrychange")}} وقتی تغییر ورودی فعلی کامل شود فعال خواهد شد.

### محدودیت‌ها

چند محدودیت درک‌شده برای Navigation API وجود دارد:

1. مشخصات فعلی در اولین بارگذاری صفحه رویداد {{domxref("Navigation.navigate_event", "navigate")}} را فعال نمی‌کند. این ممکن است برای سایت‌هایی که از رندر سمت سرور (SSR) استفاده می‌کنند مشکلی نباشد — سرور شما می‌تواند state اولیه صحیح را برگرداند که سریع‌ترین راه رساندن محتوا به کاربران است. اما سایت‌هایی که برای ساخت صفحاتشان از کد سمت کلاینت استفاده می‌کنند، ممکن است به یک تابع اضافی برای مقداردهی اولیه صفحه نیاز داشته باشند.
2. Navigation API فقط در یک فریم واحد عمل می‌کند — صفحه سطح بالا یا یک {{htmlelement("iframe")}} خاص. این موضوع پیامدهای جالبی دارد که [در مشخصات بیشتر مستند شده است](https://github.com/WICG/navigation-api#warning-backforward-are-not-always-opposites)، اما در عمل سردرگمی توسعه‌دهندگان را کاهش می‌دهد. {{domxref("History API", "", "", "nocode")}} قبلی چندین مورد مرزی گیج‌کننده دارد، مانند پشتیبانی از فریم‌ها، که Navigation API از همان ابتدا آن‌ها را مدیریت می‌کند.
3. در حال حاضر نمی‌توانید از Navigation API برای تغییر یا بازچینی برنامه‌ای فهرست تاریخچه استفاده کنید. ممکن است داشتن یک state موقت مفید باشد؛ مثلاً انتقال کاربر به یک پنجره/مودال (modal) موقت که از او اطلاعاتی می‌خواهد و سپس بازگشت به URL قبلی. در این حالت، می‌خواهید ورودی تاریخچه مربوط به آن پنجره/مودال موقت را حذف کنید تا کاربر نتواند با زدن دکمه جلو، جریان برنامه را به هم بریزد و دوباره آن را باز کند.

## رابط‌ها

- {{domxref("NavigateEvent")}} {{Experimental_Inline}}
  - : شیء رویداد مربوط به رویداد {{domxref("Navigation/navigate_event", "navigate")}} است که وقتی [هر نوع ناوبری](https://github.com/WICG/navigation-api#appendix-types-of-navigations) آغاز شود فعال می‌شود. دسترسی به اطلاعات آن ناوبری و مهم‌تر از همه متد {{domxref("NavigateEvent.intercept", "intercept()")}} را فراهم می‌کند که به شما امکان می‌دهد آنچه هنگام آغاز ناوبری رخ می‌دهد را کنترل کنید.
- {{domxref("Navigation")}} {{Experimental_Inline}}
  - : کنترل همه کنش‌های ناوبری برای `window` فعلی را در یک نقطه مرکزی فراهم می‌کند؛ از جمله آغاز برنامه‌ای ناوبری‌ها، بررسی ورودی‌های تاریخچه ناوبری و مدیریت ناوبری‌ها در حین وقوع.
- {{domxref("NavigationActivation")}} {{Experimental_Inline}}
  - : نمایانگر یک ناوبری بین‌سندی (cross-document) اخیر است. شامل نوع ناوبری و ورودی‌های تاریخچه اسناد مبدأ و مقصد است.
- {{domxref("NavigationCurrentEntryChangeEvent")}} {{Experimental_Inline}}
  - : شیء رویداد برای رویداد {{domxref("Navigation/currententrychange_event", "currententrychange")}} است که وقتی {{domxref("Navigation.currentEntry")}} تغییر کند فعال می‌شود. دسترسی به نوع ناوبری و ورودی تاریخچه قبلی که از آن ناوبری انجام شده را فراهم می‌کند.
- {{domxref("NavigationDestination")}} {{Experimental_Inline}}
  - : نمایانگر مقصدی است که در ناوبری فعلی به آن ناوبری می‌شود.
- {{domxref("NavigationHistoryEntry")}} {{Experimental_Inline}}
  - : نمایانگر یک ورودی تاریخچه ناوبری است.
- {{domxref("NavigationPrecommitController")}} {{Experimental_Inline}}
  - : رفتار بازهدایت (redirect) را برای یک مدیریت‌کننده پیش از ثبت (precommit) ناوبری تعریف می‌کند، وقتی در فراخوانی [`precommitHandler`](/en-US/docs/Web/API/NavigateEvent/intercept#precommithandler) متد {{domxref("NavigateEvent.intercept()")}} وارد می‌شود.
- {{domxref("NavigationTransition")}} {{Experimental_Inline}}
  - : نمایانگر یک ناوبری در حال انجام است.

## افزونه‌های سایر رابط‌ها

- {{domxref("Window.navigation")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : شیء {{domxref("Navigation")}} مرتبط با `window` فعلی را برمی‌گرداند. این نقطه ورود به Navigation API است.

## مثال‌ها

> [!NOTE]
> [دموی زنده Navigation API](https://mdn.github.io/dom-examples/navigation-api/) را ببینید ([مشاهده سورس دمو](https://github.com/mdn/dom-examples/tree/main/navigation-api)).

### مدیریت یک ناوبری با استفاده از `intercept()`

```js
navigation.addEventListener("navigate", (event) => {
  // We can't intercept some navigations, e.g. cross-origin navigations.
  // Return early and let the browser handle them normally.
  if (!event.canIntercept) {
    return;
  }

  // We shouldn't intercept fragment navigations or downloads.
  if (event.hashChange || event.downloadRequest !== null) {
    return;
  }

  const url = new URL(event.destination.url);

  if (url.pathname.startsWith("/articles/")) {
    event.intercept({
      async handler() {
        // The URL has already changed, so show a placeholder while
        // fetching the new content, such as a spinner or loading page
        renderArticlePagePlaceholder();

        // Fetch the new content and display when ready
        const articleContent = await getArticleContent(url.pathname);
        renderArticlePage(articleContent);
      },
    });
  }
});
```

### مدیریت پیمایش با استفاده از `scroll()`

در این مثال از رهگیری یک ناوبری، تابع `handler()` ابتدا محتوای مقاله را دریافت و رندر می‌کند، اما سپس محتوای ثانویه‌ای را هم دریافت و رندر می‌کند. منطقی است که به محض در دسترس بودن محتوای اصلی مقاله، صفحه را به آن اسکرول کنید تا کاربر بتواند با آن تعامل کند، به‌جای اینکه منتظر رندر شدن محتوای ثانویه نیز بمانید. برای این کار، یک فراخوانی {{domxref("NavigateEvent.scroll", "scroll()")}} بین این دو اضافه کرده‌ایم.

```js
navigation.addEventListener("navigate", (event) => {
  // Return early if we can't/shouldn't intercept
  if (
    !event.canIntercept ||
    event.hashChange ||
    event.downloadRequest !== null
  ) {
    return;
  }

  const url = new URL(event.destination.url);

  if (url.pathname.startsWith("/articles/")) {
    event.intercept({
      async handler() {
        const articleContent = await getArticleContent(url.pathname);
        renderArticlePage(articleContent);

        event.scroll();

        const secondaryContent = await getSecondaryContent(url.pathname);
        addSecondaryContent(secondaryContent);
      },
    });
  }
});
```

### پیمایش به یک ورودی تاریخچه خاص

```js
// On JS startup, get the key of the first loaded page
// so the user can always go back there.
const { key } = navigation.currentEntry;
backToHomeButton.onclick = () => navigation.traverseTo(key);

// Navigate away, but the button will always work.
await navigation.navigate("/another_url").finished;
```

### به‌روزرسانی state

```js
navigation.navigate(url, { state: newState });
```

یا

```js
navigation.reload({ state: newState });
```

یا اگر state مستقل از ناوبری یا بارگذاری مجدد باشد:

```js
navigation.updateCurrentEntry({ state: newState });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)