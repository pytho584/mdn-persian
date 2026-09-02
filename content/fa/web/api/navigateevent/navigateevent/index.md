---
title: "NavigateEvent: NavigateEvent() constructor"
short-title: NavigateEvent()
slug: Web/API/NavigateEvent/NavigateEvent
page-type: web-api-constructor
browser-compat: api.NavigateEvent.NavigateEvent
---

{{APIRef("Navigation API")}}

سازنده‌ی **`NavigateEvent()`** یک نمونه‌ی جدید از شیء {{domxref("NavigateEvent")}} ایجاد می‌کند.

## Syntax

```js-nolint
new NavigateEvent(type, init)
```

### پارامترها

- `type`
  - : یک رشته (string) که نوع رویداد را مشخص می‌کند.
- `init`
  - : یک شیء که علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}، دارای ویژگی‌های زیر است:
    - `canIntercept` {{optional_inline}}
      - : یک مقدار بولی (boolean) که مشخص می‌کند آیا می‌توان ناوبری را رهگیری کرد یا نه (مثلاً نمی‌توان ناوبری بین‌مبدأ (cross-origin) را رهگیری کرد). پیش‌فرض `false` است.
    - `destination`
      - : یک شیء {{domxref("NavigationDestination")}} که موقعیت مقصد ناوبری را نشان می‌دهد.
    - `downloadRequest` {{optional_inline}}
      - : نام فایل درخواست‌شده برای دانلود، در صورت ناوبری دانلودی (مانند یک عنصر {{htmlelement("a")}} یا {{htmlelement("area")}} با ویژگی `download`). پیش‌فرض `null` است.
    - `formData` {{optional_inline}}
      - : شیء {{domxref("FormData")}} که داده‌های ارسال‌شده در ارسال فرم با روش `POST` را نشان می‌دهد. پیش‌فرض `null` است.
    - `hashChange` {{optional_inline}}
      - : یک مقدار بولی که مشخص می‌کند آیا ناوبری یک ناوبری به بخش (fragment) است (یعنی به یک شناسه‌ی بخش در همان سند). پیش‌فرض `false` است.
    - `hasUAVisualTransition` {{optional_inline}}
      - : یک مقدار بولی که مشخص می‌کند آیا عامل کاربر (user agent) قبل از ارسال این رویداد یک انتقال بصری برای این ناوبری انجام داده است. پیش‌فرض `false` است.
    - `info` {{optional_inline}}
      - : مقدار داده‌ی `info` که توسط عملیات ناوبری آغازگر (مانند {{domxref("Navigation.back()")}} یا {{domxref("Navigation.navigate()")}}) ارسال شده است.
    - `navigationType` {{optional_inline}}
      - : نوع ناوبری. مقادیر ممکن: `push`، `reload`، `replace` و `traverse`. پیش‌فرض `push` است.
    - `signal`
      - : یک {{domxref("AbortSignal")}} که در صورت لغو ناوبری (مثلاً با فشار دادن دکمه‌ی «توقف» مرورگر توسط کاربر یا شروع ناوبری دیگری که باعث لغو ناوبری جاری می‌شود) قطع (abort) می‌شود.
    - `sourceElement` {{optional_inline}}
      - : یک شیء {{domxref("Element")}} که عنصر آغازگر را در مواردی که ناوبری توسط یک عنصر آغاز شده است نشان می‌دهد، یا اگر ناوبری توسط یک عنصر آغاز نشده باشد `null` است. پیش‌فرض `null`.
    - `userInitiated` {{optional_inline}}
      - : یک مقدار بولی که مشخص می‌کند آیا ناوبری توسط کاربر آغاز شده است (مثلاً با کلیک روی یک پیوند، ارسال یک فرم، یا فشار دادن دکمه‌های «بازگشت»/«رفتن به جلو» مرورگر). پیش‌فرض `false` است.

### مقدار بازگشتی

یک شیء جدید {{domxref("NavigateEvent")}}.

## مثال‌ها

یک توسعه‌دهنده از این سازنده به صورت دستی استفاده نمی‌کند. یک شیء جدید `NavigateEvent` زمانی ساخته می‌شود که یک handler در نتیجه‌ی شلیک رویداد {{domxref("Navigation.navigate_event", "navigate")}} فراخوانی شود.

```js
navigation.addEventListener("navigate", (event) => {
  // Exit early if this navigation shouldn't be intercepted,
  // e.g. if the navigation is cross-origin, or a download request
  if (shouldNotIntercept(event)) {
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

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: API Navigation](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح API Navigation](https://github.com/WICG/navigation-api/blob/main/README.md)