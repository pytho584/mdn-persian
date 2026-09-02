---
title: "Navigation: navigate() method"
short-title: navigate()
slug: Web/API/Navigation/navigate
page-type: web-api-instance-method
browser-compat: api.Navigation.navigate
---

{{APIRef("Navigation API")}}

متد **`navigate()`** از رابط {{domxref("Navigation")}} به یک URL مشخص حرکت می‌کند و هر state ارائه‌شده را در لیست ورودی‌های تاریخچه به‌روز می‌کند.

## Syntax

```js-nolint
navigate(url)
navigate(url, options)
```

### پارامترها

- `url`
  - : URL مقصد برای ناوبری. توجه داشته باشید که هنگام فراخوانی `navigate()` بر روی شیء `navigation` یک پنجره دیگر، URL نسبت به URL پنجره هدف حل می‌شود، نه URL پنجره فراخواننده. این رفتار با [History API](/en-US/docs/Web/API/History_API) مطابقت دارد، اما با رفتار [Location API](/en-US/docs/Web/API/Location) مطابقت ندارد. همچنین توجه کنید که URLهای `javascript:` به دلایل امنیتی مجاز نیستند.
- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها که شامل ویژگی‌های زیر است:
    - `state` {{optional_inline}}
      - : اطلاعات تعریف‌شده توسط توسعه‌دهنده که در {{domxref("NavigationHistoryEntry")}} مرتبط ذخیره می‌شود پس از اتمام ناوبری، و از طریق {{domxref("NavigationHistoryEntry.getState", "getState()")}} قابل بازیابی است. این می‌تواند هر نوع داده‌ای باشد. برای مثال، ممکن است بخواهید تعداد بازدید صفحه را برای اهداف تحلیلی ذخیره کنید، یا جزئیات وضعیت رابط کاربری را ذخیره کنید تا نمای صفحه دقیقاً همانطور که کاربر آخرین بار رها کرده بود نمایش داده شود. هر داده ذخیره‌شده در `state` باید [ساختار-قابل-کلونینگ](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) باشد.
    - `info` {{optional_inline}}
      - : اطلاعات تعریف‌شده توسط توسعه‌دهنده که به رویداد {{domxref("Navigation/navigate_event", "navigate")}} ارسال می‌شود و در {{domxref("NavigateEvent.info")}} در دسترس قرار می‌گیرد. این می‌تواند هر نوع داده‌ای باشد. برای مثال، ممکن است بخواهید محتوای تازه‌ناوبری‌شده را با یک انیمیشن متفاوت بسته به نحوه ناوبری به آن (کشیدن به چپ، کشیدن به راست، یا رفتن به خانه) نمایش دهید. یک رشته که نشان‌دهنده انیمیشن مورد استفاده است می‌تواند به عنوان `info` ارسال شود.
    - `history` {{optional_inline}}
      - : یک مقدار شمارشی که رفتار تاریخچه این ناوبری را تنظیم می‌کند. مقادیر موجود عبارتند از:
        - `auto`: مقدار پیش‌فرض؛ معمولاً یک ناوبری `push` انجام می‌دهد اما در شرایط خاص یک ناوبری `replace` انجام می‌دهد (به توضیحات `NotSupportedError` در زیر مراجعه کنید).
        - `push`: یک {{domxref("NavigationHistoryEntry")}} جدید به لیست ورودی‌ها اضافه می‌کند، یا در شرایط خاص شکست می‌خورد (به توضیحات `NotSupportedError` در زیر مراجعه کنید).
        - `replace`: ورودی فعلی {{domxref("NavigationHistoryEntry")}} را جایگزین می‌کند.

### مقدار بازگشتی

یک شیء با ویژگی‌های زیر:

- `committed`
  - : یک {{jsxref("Promise")}} که زمانی به انجام می‌رسد که URL قابل مشاهده تغییر کرده و یک {{domxref("NavigationHistoryEntry")}} جدید ایجاد شده باشد.
- `finished`
  - : یک {{jsxref("Promise")}} که زمانی به انجام می‌رسد که تمام قول‌های بازگشتی توسط handler `intercept()` به انجام برسند. این معادل با به‌انجام‌رسیدن قول {{domxref("NavigationTransition.finished")}} است، زمانی که رویداد {{domxref("Navigation/navigatesuccess_event", "navigatesuccess")}} رخ می‌دهد.

هر یک از این قول‌ها در صورت ناموفق بودن ناوبری به دلایلی رد می‌شوند.

### استثناها

- `DataCloneError` {{domxref("DOMException")}}
  - : اگر پارامتر `state` حاوی مقادیری باشد که ساختار-قابل-کلونینگ نیستند، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر سند در حال حاضر فعال نباشد، پرتاب می‌شود.
- `SyntaxError` {{domxref("DOMException")}}
  - : اگر پارامتر `url` یک URL معتبر نباشد، پرتاب می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - گزینه `history` روی `push` تنظیم شده باشد و مرورگر در حال نمایش سند اولیه `about:blank` باشد.
    - طرح `url` برابر با `javascript` باشد.

## مثال‌ها

### تنظیم دکمه خانه

```js
function initHomeBtn() {
  // Get the key of the first loaded entry
  // so the user can always go back to this view.
  const { key } = navigation.currentEntry;
  backToHomeButton.onclick = () => {
    navigation.traverseTo(key);
  };
}
// Intercept navigate events, such as link clicks, and
// replace them with single-page navigations
navigation.addEventListener("navigate", (event) => {
  event.intercept({
    async handler() {
      // Navigate to a different view,
      // but the "home" button will always work.
    },
  });
});
```

### یک دکمه بازگشت هوشمند

یک دکمه "بازگشت" که توسط صفحه ارائه می‌شود می‌تواند شما را به عقب برگرداند، حتی پس از بارگذاری مجدد، با بررسی ورودی‌های تاریخچه قبلی:

```js
backButtonEl.addEventListener("click", () => {
  if (
    navigation.entries()[navigation.currentEntry.index - 1]?.url ===
    "/product-listing"
  ) {
    navigation.back();
  } else {
    // If the user arrived here in some other way
    // e.g. by typing the URL directly:
    navigation.navigate("/product-listing", { history: "replace" });
  }
});
```

### استفاده از info و state

```js
async function navigateHandler() {
  await navigation.navigate(url, {
    info: { animation: "swipe-right" },
    state: { infoPaneOpen: true },
  }).finished;

  // Update application state
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح Navigation API](https://github.com/WICG/navigation-api/blob/main/README.md)