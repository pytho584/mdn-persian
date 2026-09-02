---
title: "NavigationCurrentEntryChangeEvent: NavigationCurrentEntryChangeEvent() constructor"
---

{{APIRef("Navigation API")}}

سازندهٔ **`NavigationCurrentEntryChangeEvent()`** یک شیء جدید از نوع {{domxref("NavigationCurrentEntryChangeEvent")}} می‌سازد.

## نحو

```js-nolint
new NavigationCurrentEntryChangeEvent(type, init)
```

### پارامترها

- `type`
  - : رشته‌ای است که نوع رویداد را نشان می‌دهد.
- `init`
  - : شیئی که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، ویژگی‌های زیر را دارد:
    - `from`
      - : یک شیء {{domxref("NavigationHistoryEntry")}} که موقعیتی را نشان می‌دهد که به آن پیمایش شده است.
    - `navigationType` {{optional_inline}}
      - : نوع پیمایشی که منجر به این تغییر شده است. مقادیر ممکن عبارت‌اند از `push`، `reload`، `replace` و `traverse`. پیش‌فرض آن `null` است.

### مقدار بازگشتی

یک شیء جدید {{domxref("NavigationCurrentEntryChangeEvent")}}.

## مثال‌ها

توسعه‌دهندگان معمولاً این سازنده را به‌صورت دستی استفاده نمی‌کنند. یک شیء `NavigationCurrentEntryChangeEvent` زمانی ساخته می‌شود که در نتیجهٔ به‌وقوع‌پیوستن رویداد {{domxref("Navigation.currententrychange_event", "currententrychange")}}، یک کنترل‌کننده فراخوانی شود.

```js
navigation.addEventListener("currententrychange", (event) => {
  console.log(event.navigationType);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)