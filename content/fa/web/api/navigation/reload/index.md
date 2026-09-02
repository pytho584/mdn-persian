---
title: "Navigation: reload() method"
short-title: reload()
slug: Web/API/Navigation/reload
page-type: web-api-instance-method
browser-compat: api.Navigation.reload
---

{{APIRef("Navigation API")}}

متد **`reload()`** در رابط {{domxref("Navigation")}}، URL فعلی را بارگذاری مجدد می‌کند و هر state ارائه‌شده را در فهرست entries تاریخچه به‌روزرسانی می‌کند.

توجه داشته باشید که `reload()` رویداد [`popstate`](/en-US/docs/Web/API/Window/popstate_event) را فعال نمی‌کند؛ زیرا این رویداد فقط برای ناوبری‌های نرمی (soft navigations) فعال می‌شود که باعث «عبور» (traversal) از entries تاریخچه می‌شوند.

## Syntax

```js-nolint
reload()
reload(options)
```

### Parameters

- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها که شامل ویژگی‌های زیر است:
    - `state` {{optional_inline}}
      - : اطلاعات تعریف‌شده توسط توسعه‌دهنده که پس از تکمیل ناوبری در {{domxref("NavigationHistoryEntry")}} مرتبط ذخیره می‌شود و از طریق {{domxref("NavigationHistoryEntry.getState", "getState()")}} قابل بازیابی است.
        این می‌تواند هر نوع داده‌ای باشد. به عنوان مثال، ممکن است بخواهید تعداد بازدیدهای صفحه را برای اهداف تحلیل (analytics) ذخیره کنید، یا جزئیات وضعیت UI را ذخیره کنید تا نمایش دقیقاً همان گونه باشد که کاربر آخرین بار آن را ترک کرده است.
        هر داده ذخیره‌شده در `state` باید [ساختار-کلون‌پذیر (structured-cloneable)](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) باشد.
    - `info` {{optional_inline}}
      - : اطلاعات تعریف‌شده توسط توسعه‌دهنده که به رویداد {{domxref("Navigation/navigate_event", "navigate")}} منتقل می‌شود و در {{domxref("NavigateEvent.info")}} در دسترس قرار می‌گیرد.
        این می‌تواند هر نوع داده‌ای باشد. به عنوان مثال، ممکن است بخواهید محتوای تازه‌ناوبری‌شده را با انیمیشن متفاوتی بسته به نحوه ناوبری به آن (کشیدن به چپ، کشیدن به راست، یا بازگشت به خانه) نمایش دهید.
        یک رشته که نشان می‌دهد کدام انیمیشن استفاده شود می‌تواند به عنوان `info` ارسال شود.

### Return value

یک شیء با ویژگی‌های زیر:

- `committed`
  - : یک {{jsxref("Promise")}} که وقتی URL قابل مشاهده تغییر کند و یک {{domxref("NavigationHistoryEntry")}} جدید ایجاد شود، fulfilled می‌شود.
- `finished`
  - : یک {{jsxref("Promise")}} که وقتی تمام promiseهای بازگردانده‌شده توسط هندلر `intercept()` fulfilled شوند، fulfilled می‌شود. این معادل fulfilled شدن promise {{domxref("NavigationTransition.finished")}}، زمانی که رویداد {{domxref("Navigation/navigatesuccess_event", "navigatesuccess")}} رخ می‌دهد، است.

هر یک از این promiseها در صورت شکست ناوبری به دلیلی، reject می‌شوند.

### Exceptions

- `DataCloneError` {{domxref("DOMException")}}
  - : اگر پارامتر `state` شامل مقادیری باشد که ساختار-کلون‌پذیر نیستند، پرتاب می‌شود.

## Examples

### استفاده از info و state

```js
async function handleReload() {
  await navigation.reload({
    info: { animation: "fade-in" },
    state: { infoPaneOpen: true },
  }).finished;

  // Update application state
  // …
}
```

بارگذاری مجدد صفحه و افزودن یک آیتم state جدید:

```js
async function handleReload() {
  await navigation.reload({
    state: { ...navigation.currentEntry.getState(), newState: 3 },
  }).finished;

  // Update application state
  // …
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)