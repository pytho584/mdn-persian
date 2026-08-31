---
title: "BackgroundFetchUpdateUIEvent: BackgroundFetchUpdateUIEvent() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchUpdateUIEvent/BackgroundFetchUpdateUIEvent"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchUpdateUIEvent: BackgroundFetchUpdateUIEvent() constructor"
short-title: BackgroundFetchUpdateUIEvent()
slug: Web/API/BackgroundFetchUpdateUIEvent/BackgroundFetchUpdateUIEvent
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.BackgroundFetchUpdateUIEvent.BackgroundFetchUpdateUIEvent
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

سازندهٔ **`BackgroundFetchUpdateUIEvent()`** یک شیء جدید از نوع {{domxref("BackgroundFetchUpdateUIEvent")}} می‌سازد. این سازنده معمولاً به‌طور مستقیم استفاده نمی‌شود، زیرا مرورگر این اشیاء را به‌طور خودکار ساخته و آن‌ها را به فراخوانی‌های رویداد background fetch ارائه می‌دهد.

## نحو (Syntax)

```js-nolint
new BackgroundFetchEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای شامل نام رویداد.
    این مقدار به حروف بزرگ و کوچک حساس است و مرورگر آن را روی `backgroundfetchsuccess` یا `backgroundfetchfail` تنظیم می‌کند.
- `options`
  - : شیءای که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("ExtendableEvent/ExtendableEvent", "ExtendableEvent()")}}_، دارای ویژگی‌های زیر است:
    - `registration`
      - : یک شیء {{domxref("BackgroundFetchRegistration")}}.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("BackgroundFetchUpdateUIEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}