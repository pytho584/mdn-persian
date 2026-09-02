---
title: "NavigateEvent: intercept() method"
---
---
title: "NavigateEvent: intercept() method"
short-title: intercept()
slug: Web/API/NavigateEvent/intercept
page-type: web-api-instance-method
browser-compat: api.NavigateEvent.intercept
---

{{APIRef("Navigation API")}}

متد **`intercept()`** در رابط {{domxref("NavigateEvent")}} این ناوبری را رهگیری کرده و آن را به یک ناوبری در همان سند (same-document) به سمت URL {{domxref("NavigationDestination.url", "destination")}} تبدیل می‌کند.

## سینتکس

```js-nolint
intercept()
intercept(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها شامل ویژگی‌های زیر:
    - `handler` {{optional_inline}}
      - : یک تابع callback که تعریف می‌کند رفتار مدیریت ناوبری باید چه باشد؛ یک promise برمی‌گرداند. این تابع پس از به‌روزرسانی ویژگی {{domxref("Navigation.currentEntry", "currentEntry")}} اجرا می‌شود.
    - `precommitHandler` {{optional_inline}}
      - : یک تابع callback که هر رفتاری را که باید درست قبل از قطعی‌شدن (committed) ناوبری رخ دهد تعریف می‌کند؛ یک شیء {{domxref("NavigationPrecommitController")}} را به عنوان آرگومان می‌پذیرد و یک promise برمی‌گرداند. این تابع قبل از به‌روزرسانی ویژگی {{domxref("Navigation.currentEntry", "currentEntry")}} اجرا می‌شود.
    - `focusReset` {{optional_inline}}
      - : رفتار تمرکز (focus) ناوبری را تعریف می‌کند. این گزینه می‌تواند یکی از مقادیر زیر را بگیرد:
        - `after-transition`
          - : پس از اینکه promise بازگشتی توسط تابع handler شما resolve شد، مرورگر اولین عنصر دارای ویژگی [`autofocus`](/en-US/docs/Web/HTML/Reference/Global_attributes/autofocus) را فوکوس می‌کند، یا اگر هیچ عنصری `autofocus` نداشته باشد، عنصر {{htmlelement("body")}} را فوکوس می‌کند. این مقدار پیش‌فرض است.
        - `manual`
          - : رفتار پیش‌فرض را غیرفعال می‌کند.
    - `scroll` {{optional_inline}}
      - : رفتار اسکرول ناوبری را تعریف می‌کند. این گزینه می‌تواند یکی از مقادیر زیر را بگیرد:
        - `after-transition`
          - : به مرورگر اجازه می‌دهد تا اسکرول را مدیریت کند؛ مثلاً اگر URL حاوی یک fragment باشد به شناسه‌ی قطعه مربوطه اسکرول کند، یا اگر صفحه دوباره بارگذاری شود یا صفحه‌ای از تاریخچه مجدداً بازدید شود، موقعیت اسکرول را به همان مکان قبلی بازگرداند. این مقدار پیش‌فرض است.
        - `manual`
          - : رفتار پیش‌فرض را غیرفعال می‌کند.

### مقدار بازگشتی

هیچ (`undefined`).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("Document")}} فعلی هنوز فعال نیست، یا اگر ناوبری لغو شده باشد، پرتاب می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که:
    - رویداد توسط یک فراخوانی {{domxref("EventTarget.dispatchEvent", "dispatchEvent()")}} توزیع شده باشد، نه توسط عامل کاربر (user agent).
    - ناوبری قابل رهگیری نباشد ({{domxref("NavigateEvent.canIntercept")}} برابر `false` است).
    - یک callback `precommitHandler()` روی یک رویداد غیرقابل‌لغو ارائه شده باشد ({{domxref("Event.cancelable")}} برابر `false` است).

## توضیحات

متد `intercept()` برای پیاده‌سازی رفتار ناوبری در همان سند (SPA) هنگام وقوع یک ناوبری استفاده می‌شود؛ مثلاً وقتی یک پیوند کلیک می‌شود، یک فرم ارسال می‌شود، یا یک ناوبری برنامه‌ای (programmatic) آغاز می‌شود (با استفاده از {{domxref("History.pushState()")}}، {{domxref("Window.location")}} و غیره).

این کار از طریق چند callback مختلف یعنی `handler()` و `precommitHandler()` انجام می‌شود.

### مدیریت ناوبری‌های فوری با `handler()`

callback `handler()` در پاسخ به یک ناوبری قطعی‌شده (committed) اجرا می‌شود. این callback پس از به‌روزرسانی ویژگی {{domxref("Navigation.currentEntry", "currentEntry")}} اجرا می‌شود؛ یعنی یک URL جدید در رابط کاربری مرورگر نمایش داده می‌شود و تاریخچه با یک ورودی جدید به‌روزرسانی می‌شود.

یک مثال معمولی به این صورت است که امکان رندر و بارگذاری محتوای خاص را در پاسخ به یک ناوبری مشخص فراهم می‌کند:

```js
navigation.addEventListener("navigate", (event) => {
  const url = new URL(event.destination.url);

  if (url.pathname.startsWith("/articles/")) {
    event.intercept({
      async handler() {
        // Fetch the new content and display when ready
        const articleContent = await getArticleContent(url.pathname);
        renderArticlePage(articleContent);
      },
    });
  }

  // Include multiple conditions for different page types here, as needed
});
```

`handler()` باید برای پیاده‌سازی رفتار ناوبری استفاده شود که ناوبری به آن متعهد شده است: باید چیزی جدید به کاربر نمایش داده شود.

### مدیریت اقدامات قبل از قطعی‌شدن با `precommitHandler()`

با این حال، ممکن است بخواهید ناوبری در حال انجام را تغییر دهید یا لغو کنید، یا در حالی که ناوبری در جریان است و قبل از قطعی‌شدن آن کاری انجام دهید. این نوع سناریو را می‌توان با callback `precommitHandler()` مدیریت کرد؛ این callback قبل از به‌روزرسانی ویژگی {{domxref("Navigation.currentEntry", "currentEntry")}} و نمایش مکان جدید در رابط کاربری مرورگر اجرا می‌شود.

مثلاً اگر کاربر به صفحه‌ای محدود پیمایش کند و وارد سیستم نشده باشد، ممکن است بخواهید مرورگر را به صفحه ورود هدایت کنید. این کار می‌تواند به صورت زیر انجام شود:

```js
navigation.addEventListener("navigate", (event) => {
  const url = new URL(event.destination.url);

  if (url.pathname.startsWith("/restricted/") && !userSignedIn) {
    event.intercept({
      async precommitHandler(controller) {
        controller.redirect("/signin/", {
          state: "signin-redirect",
          history: "push",
        });
      },
    });
  }
});
```

این الگو ساده‌تر از جایگزین آن، یعنی لغو ناوبری اصلی و شروع یک ناوبری جدید به مکان هدایت‌شده است، زیرا از بروز حالت میانی جلوگیری می‌کند. به عنوان مثال، فقط یک رویداد {{domxref("Navigation.navigatesuccess_event", "navigatesuccess")}} یا {{domxref("Navigation.navigateerror_event", "navigateerror")}} فعال می‌شود، و اگر ناوبری توسط فراخوانی {{domxref("Navigation.navigate()")}} آغاز شده باشد، promise فقط پس از رسیدن به مقصد هدایت محقق می‌شود.

callback `precommitHandler()` یک شیء {{domxref("NavigationPrecommitController")}} را به عنوان آرگومان می‌گیرد که شامل یک متد {{domxref("NavigationPrecommitController.redirect", "redirect()")}} است. متد `redirect()` دو پارامتر می‌گیرد: یک رشته که URL هدف هدایت است، و یک شیء گزینه‌های اختیاری که می‌تواند رفتار state و history را مشخص کند.

`precommitHandler()` عموماً هر اصلاحیه‌ای را که قبل از نمایش واقعی URL مقصد در مرورگر لازم است بر روی رفتار ناوبری انجام می‌دهد، ناوبری را لغو می‌کند یا طبق نیاز به جای دیگری هدایت می‌کند.

> [!NOTE]
> از آنجا که `precommitHandler()` می‌تواند برای لغو ناوبری استفاده شود، فقط زمانی به‌درستی کار می‌کند که ویژگی {{domxref("Event.cancelable")}} رویداد برابر `true` باشد. فراخوانی `intercept()` با یک `precommitHandler()` روی یک رویداد غیرقابل‌لغو باعث پرتاب `SecurityError` می‌شود.

### زمان‌بندی اقدامات پس از قطعی‌شدن در `precommitHandler()`

همانطور که در بالا دیدیم، می‌توانید یک callback `handler()` در شیء ارسال‌شده به متد `intercept()` مشخص کنید تا پس از قطعی‌شدن ناوبری اقداماتی انجام شود. این رویکرد زمانی خوب کار می‌کند که اقدامات مورد نیاز پس از قطعی‌شدن به هیچ اقدامات اجراشده در مرحله قبل از قطعی‌شدن وابسته نباشند. اگر وابسته باشند، می‌توانید از {{domxref("NavigationPrecommitController.addHandler()")}} در `precommitHandler()` برای افزودن پویای یک handler استفاده کنید که پس از قطعی‌شدن ناوبری اجرا خواهد شد.

برای مثال، کدی را در نظر بگیرید که مثال قبلی هدایت کاربر خارج‌شده از سیستم به صفحه ورود را گسترش می‌دهد. این کد از `addHandler()` برای افزودن یک callback handler پس از قطعی‌شدن استفاده می‌کند که پیامی توضیح‌دهنده دلیل هدایت را نشان می‌دهد. توجه داشته باشید که handler فقط در مورد خاص هدایت به صفحه ورود اجرا می‌شود.

```js
navigation.addEventListener("navigate", (event) => {
  const url = new URL(event.destination.url);

  if (url.pathname.startsWith("/restricted/") && !userSignedIn) {
    event.intercept({
      async precommitHandler(controller) {
        controller.redirect("/signin/", {
          state: "signin-redirect",
          history: "push",
        });

        // Use addHandler to trigger logic once the /signin/ page commits
        controller.addHandler(() => {
          showMessage("Please sign in to view that content.");
        });
      },
    });
  }
});
```

### پاسخ به موفقیت یا شکست ناوبری

هنگامی که promise های بازگشتی توسط توابع handler متد `intercept()` محقق می‌شوند، رویداد {{domxref("Navigation/navigatesuccess_event", "navigatesuccess")}} روی شیء `Navigation` فعال می‌شود و به شما امکان می‌دهد پس از اتمام موفقیت‌آمیز ناوبری کد تمیزکاری اجرا کنید. اگر آن promise ها رد شوند، به این معنی است که ناوبری ناموفق بوده است؛ در عوض رویداد {{domxref("Navigation/navigateerror_event", "navigateerror")}} فعال می‌شود و به شما امکان می‌دهد مورد شکست را به‌راحتی مدیریت کنید.

همچنین یک ویژگی `finished` روی مقدار بازگشتی متدهای ناوبری (مانند {{domxref("Navigation.navigate()")}}) وجود دارد که همزمان با فعال‌شدن رویدادهای مذکور محقق یا رد می‌شود و مسیر دیگری برای مدیریت موارد موفقیت و شکست فراهم می‌کند.

### تعامل بین `precommitHandler()` و `handler()`

هر دو callback یعنی `precommitHandler()` و `handler()` می‌توانند در یک فراخوانی `intercept()` گنجانده شوند. در چنین مواردی، ترتیب عملیات به صورت زیر است:

1. ابتدا، handler مربوط به `precommitHandler()` اجرا می‌شود.
   - وقتی promise مربوط به `precommitHandler()` محقق شود، ناوبری قطعی می‌شود.
   - اگر `precommitHandler()` رد شود، رویداد `navigateerror` فعال می‌شود، promise های `committed` و `finished` رد می‌شوند و ناوبری لغو می‌شود.

2. وقتی ناوبری قطعی می‌شود، یک {{domxref("NavigationHistoryEntry")}} جدید برای آن ناوبری ایجاد می‌شود و promise `committed` آن محقق می‌شود.

3. سپس، promise مربوط به `handler()` اجرا می‌شود.
   - وقتی promise مربوط به `handler()` محقق شود و رویداد `navigatesuccess` فعال شود، promise `finished` ناوبری نیز محقق می‌شود تا نشان دهد ناوبری به پایان رسیده است.
   - اگر `handler()` رد شود، رویداد `navigateerror` فعال می‌شود، promise `finished` رد می‌شود و ناوبری لغو می‌شود.

توجه داشته باشید که فرآیند فوق حتی در چندین فراخوانی `intercept()` روی یک `NavigateEvent` و برای callback های `handler()` اضافه‌شده در `precommitHandler()` نیز حفظ می‌شود. ابتدا همه callback های `precommitHandler()` فراخوانی می‌شوند و وقتی همه آن‌ها resolve شوند، ناوبری قطعی می‌شود و همه callback های `handler()` فراخوانی می‌شوند.

### کنترل رفتار تمرکز

به‌طور پیش‌فرض، پس از وقوع یک ناوبری که با `intercept()` مدیریت شده است، تمرکز سند (document focus) به اولین عنصر در DOM که دارای ویژگی [`autofocus`](/en-US/docs/Web/HTML/Reference/Global_attributes/autofocus) است بازنشانی می‌شود، یا اگر هیچ ویژگی `autofocus` تنظیم نشده باشد، به عنصر {{htmlelement("body")}} بازنشانی می‌شود. اگر می‌خواهید این رفتار را نادیده بگیرید و موقعیت تمرکز قابل‌دسترس‌تری را در ناوبری به صورت دستی پیاده‌سازی کنید (مثلاً عنوان جدید سطح بالا)، می‌توانید با تنظیم گزینه `focusReset` بر روی `manual` این کار را انجام دهید.

```js
navigation.addEventListener("navigate", (event) => {
  const url = new URL(event.destination.url);

  if (url.pathname.startsWith("/articles/")) {
    event.intercept({
      focusReset: manual,
      async handler() {
        // Fetch the new content and display when ready
        const articleContent = await getArticleContent(url.pathname);
        renderArticlePage(articleContent);
        // Handle page focus with a custom function
        setPageFocus();
      },
    });
  }
});
```

### کنترل رفتار اسکرول

پس از تکمیل ناوبری `intercept()`، رفتار اسکرول زیر رخ می‌دهد:

- برای ناوبری‌های `push` و `replace` (به {{domxref("Navigation.navigate()")}} مراجعه کنید)، مرورگر سعی می‌کند به fragment مشخص‌شده در `event.destination.url` اسکرول کند. اگر fragment موجود نباشد، موقعیت اسکرول را به بالای صفحه بازنشانی می‌کند.
- برای ناوبری‌های {{domxref("Navigation.traverseTo", "traverse")}} و {{domxref("Navigation.reload", "reload")}}، رفتار مشابه ناوبری‌های `push` و `replace` است، اما مرورگر منطق بازیابی اسکرول خود را تا زمان محقق‌شدن promise `intercept()` به تأخیر می‌اندازد. اگر promise رد شود، هیچ بازیابی اسکرولی انجام نمی‌دهد. اگر کاربر در طول انتقال اسکرول کرده باشد، هیچ بازیابی اسکرولی انجام نخواهد شد.

اگر می‌خواهید این رفتار را خاموش کنید، می‌توانید با تنظیم گزینه `scroll` بر روی `manual` این کار را انجام دهید.

```js
navigation.addEventListener("navigate", (event) => {
  const url = new URL(event.destination.url);

  if (url.pathname.startsWith("/articles/")) {
    event.intercept({
      scroll: manual,
      async handler() {
        // Fetch the new content and display when ready
        const articleContent = await getArticleContent(url.pathname);
        renderArticlePage(articleContent);
        // Handle scroll behavior with a custom function
        setScroll();
      },
    });
  }
});
```

اگر می‌خواهید رفتار اسکرول پیش‌فرض شرح‌داده‌شده در بالا را به صورت دستی فعال کنید (شاید بخواهید قبل از اتمام کامل ناوبری، موقعیت اسکرول را به بالای صفحه بازنشانی کنید)، می‌توانید با فراخوانی {{domxref("NavigateEvent.scroll()")}} این کار را انجام دهید.

## مثال‌ها

### مدیریت ناوبری با استفاده از `