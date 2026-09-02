Here is the Persian translation of the MDN documentation for the NavigateEvent signal property:

---

---
title: "NavigateEvent: signal property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/NavigateEvent/signal"
---

---
title: "NavigateEvent: signal property"
short-title: signal
slug: Web/API/NavigateEvent/signal
page-type: web-api-instance-property
browser-compat: api.NavigateEvent.signal
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`signal`** در رابط {{domxref("NavigateEvent")}} یک {{domxref("AbortSignal")}} برمی‌گرداند که در صورت لغو شدن ناوبری (مثلاً با فشردن دکمه «توقف» توسط کاربر در مرورگر، یا شروع یک ناوبری دیگر که منجر به لغو ناوبری جاری می‌شود) قطع (abort) خواهد شد.

## مقدار

یک شیء {{domxref("AbortSignal")}}.

## مثال‌ها

ایده کلی در اینجا این است که می‌توان ویژگی `signal` را به یک عملیات {{domxref("Window/fetch", "fetch()")}} مرتبط ارسال کرد تا در صورت لغو ناوبری، عملیات `fetch()` به‌طور امن قطع شود و از هدر رفتن پهنای باند برای دریافت‌هایی (fetch) که دیگر موردنیاز نیستند جلوگیری به عمل آید.

```js
navigation.addEventListener("navigate", (event) => {
  event.intercept({
    async handler() {
      // …

      await fetch(`/img/some-image.jpg`, { signal: event.signal });

      // …
    },
  });
});
```

> [!NOTE]
> برای یک مثال دقیق‌تر، بخش [Example: next/previous buttons](https://github.com/WICG/navigation-api#example-nextprevious-buttons) را مشاهده کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)