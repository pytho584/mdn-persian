---
title: "NavigateEvent"
---

---
title: NavigateEvent
slug: Web/API/NavigateEvent
page-type: web-api-interface
browser-compat: api.NavigateEvent
---

{{APIRef("Navigation API")}}

رابط **`NavigateEvent`** از {{domxref("Navigation API", "API ناوبری", "", "nocode")}}، شیء رویداد برای رویداد {{domxref("Navigation/navigate_event", "navigate")}} است که زمانی که [هر نوع ناوبری](https://github.com/WICG/navigation-api#appendix-types-of-navigations) آغاز می‌شود (شامل استفاده از ویژگی‌های {{domxref("History API", "API تاریخچه", "", "nocode")}} مانند {{domxref("History.go()")}})، به وقوع می‌پیوندد. `NavigateEvent` دسترسی به اطلاعات مربوط به آن ناوبری را فراهم می‌کند و به توسعه‌دهندگان اجازه می‌دهد تا مدیریت ناوبری را رهگیری و کنترل کنند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("NavigateEvent.NavigateEvent", "NavigateEvent()")}}
  - : یک نمونه جدید از شیء `NavigateEvent` ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{DOMxRef("Event")}} به ارث می‌برد._

- {{domxref("NavigateEvent.canIntercept", "canIntercept")}} {{ReadOnlyInline}}
  - : اگر ناوبری قابل رهگیری باشد `true` و در غیر این صورت `false` برمی‌گرداند (مثلاً نمی‌توانید یک ناوبری میان‌مبدأ(Cross-Origin) را رهگیری کنید).
- {{domxref("NavigateEvent.destination", "destination")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("NavigationDestination")}} برمی‌گرداند که مقصد ناوبری را نشان می‌دهد.
- {{domxref("NavigateEvent.downloadRequest", "downloadRequest")}} {{ReadOnlyInline}}
  - : نام فایل درخواست‌شده برای دانلود را در صورت ناوبری دانلودی (مثلاً یک عنصر {{htmlelement("a")}} یا {{htmlelement("area")}} با ویژگی `download`)، یا در غیر این صورت `null` برمی‌گرداند.
- {{domxref("NavigateEvent.formData", "formData")}} {{ReadOnlyInline}}
  - : شیء {{domxref("FormData")}} نمایانگر داده‌های ارسال‌شده در صورت ارسال فرم با روش `POST`، یا در غیر این صورت `null` برمی‌گرداند.
- {{domxref("NavigateEvent.hashChange", "hashChange")}} {{ReadOnlyInline}}
  - : اگر ناوبری یک ناوبری قطعه (fragment) باشد (یعنی به یک شناسه قطعه در همان سند)، `true` و در غیر این صورت `false` برمی‌گرداند.
- {{domxref("NavigateEvent.hasUAVisualTransition", "hasUAVisualTransition")}} {{ReadOnlyInline}}
  - : اگر عامل کاربر (user agent) یک انتقال بصری برای این ناوبری قبل از ارسال این رویداد انجام داده باشد، `true` و در غیر این صورت `false` برمی‌گرداند.
- {{domxref("NavigateEvent.info", "info")}} {{ReadOnlyInline}}
  - : مقدار داده `info` را که توسط عملیات ناوبری آغازگر (مثلاً {{domxref("Navigation.back()")}} یا {{domxref("Navigation.navigate()")}}) ارسال شده است، یا اگر داده `info` ارسال نشده باشد `undefined` برمی‌گرداند.
- {{domxref("NavigateEvent.navigationType", "navigationType")}} {{ReadOnlyInline}}
  - : نوع ناوبری را برمی‌گرداند — `push`، `reload`، `replace`، یا `traverse`.
- {{domxref("NavigateEvent.signal", "signal")}} {{ReadOnlyInline}}
  - : یک {{domxref("AbortSignal")}} برمی‌گرداند که اگر ناوبری لغو شود (مثلاً با فشار دادن دکمه "توقف" مرورگر توسط کاربر، یا شروع ناوبری دیگر و لغو ناوبری جاری)، قطع (abort) می‌شود.
- {{domxref("NavigateEvent.sourceElement", "sourceElement")}} {{ReadOnlyInline}}
  - : زمانی که ناوبری توسط یک عنصر آغاز شده باشد (مثلاً کلیک روی یک پیوند)، یک شیء {{domxref("Element")}} نمایانگر عنصر آغازگر را برمی‌گرداند.
- {{domxref("NavigateEvent.userInitiated", "userInitiated")}} {{ReadOnlyInline}}
  - : اگر ناوبری توسط کاربر آغاز شده باشد (مثلاً با کلیک روی یک پیوند، ارسال فرم، یا فشار دادن دکمه‌های "بازگشت"/"رفتن به جلو" مرورگر)، `true` و در غیر این صورت `false` برمی‌گرداند.

## روش‌های نمونه

_روش‌ها را از والد خود، {{DOMxRef("Event")}} به ارث می‌برد._

- {{domxref("NavigateEvent.intercept", "intercept()")}}
  - : این ناوبری را رهگیری می‌کند و آن را به یک ناوبری درون‌سندی به آدرس {{domxref("NavigationDestination.url", "مقصد")}} URL تبدیل می‌کند. می‌تواند توابع مدیریت‌کننده (handler) را بپذیرد که رفتار مدیریت ناوبری را تعریف می‌کنند، به علاوه گزینه‌های `focusReset` و `scroll` برای فعال یا غیرفعال کردن رفتار پیش‌فرض مرورگر در مورد فوکوس و اسکرول.
- {{domxref("NavigateEvent.scroll", "scroll()")}}
  - : می‌تواند برای راه‌اندازی دستی رفتار اسکرول مبتنی بر مرورگر که در پاسخ به ناوبری رخ می‌دهد، فراخوانی شود، اگر می‌خواهید قبل از تکمیل مدیریت ناوبری انجام شود.

## مثال‌ها

### مدیریت ناوبری با استفاده از `intercept()`

```js
navigation.addEventListener("navigate", (event) => {
  // اگر این ناوبری نباید رهگیری شود، زود خارج شو
  // مثلاً اگر ناوبری cross-origin یا یک درخواست دانلود است
  if (shouldNotIntercept(event)) return;

  const url = new URL(event.destination.url);

  if (url.pathname.startsWith("/articles/")) {
    event.intercept({
      async handler() {
        // URL قبلاً تغییر کرده است، بنابراین یک مکان‌نما نشان بده
        // در حین واکشی محتوای جدید، مانند یک اسپینر یا صفحه بارگذاری
        renderArticlePagePlaceholder();

        // محتوای جدید را واکشی کن و وقتی آماده شد نمایش بده
        const articleContent = await getArticleContent(url.pathname);
        renderArticlePage(articleContent);
      },
    });
  }
});
```

> [!NOTE]
> قبل از در دسترس بودن API ناوبری، برای انجام کاری مشابه باید به تمام رویدادهای کلیک روی پیوندها گوش می‌دادید، `e.preventDefault()` را اجرا می‌کردید، فراخوانی مناسب {{domxref("History.pushState()")}} را انجام می‌دادید، و سپس نمای صفحه را بر اساس URL جدید تنظیم می‌کردید. و این کار همه ناوبری‌ها را مدیریت نمی‌کرد – فقط کلیک‌های پیوند آغاز شده توسط کاربر.

### مدیریت اسکرول با استفاده از `scroll()`

در این مثال از رهگیری یک ناوبری، تابع `handler()` با واکشی و نمایش محتوای مقاله شروع می‌شود، اما سپس محتوای ثانویه را بعداً واکشی و نمایش می‌دهد. منطقی است که صفحه را به محض در دسترس بودن محتوای اصلی مقاله اسکرول کنیم تا کاربر بتواند با آن تعامل داشته باشد، به جای اینکه منتظر بمانیم تا محتوای ثانویه نیز نمایش داده شود. برای رسیدن به این هدف، یک فراخوانی {{domxref("NavigateEvent.scroll", "scroll()")}} بین دو بخش اضافه کرده‌ایم.

```js
navigation.addEventListener("navigate", (event) => {
  if (shouldNotIntercept(event)) return;
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

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کاربر: API ناوبری](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح API ناوبری](https://github.com/WICG/navigation-api/blob/main/README.md)
- [دموی زنده API ناوبری](https://mdn.github.io/dom-examples/navigation-api/) ([مشاهده منبع دمو](https://github.com/mdn/dom-examples/tree/main/navigation-api))