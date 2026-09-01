---
title: "HIDConnectionEvent: HIDConnectionEvent() constructor"
---

---
title: "HIDConnectionEvent: HIDConnectionEvent() constructor"
short-title: HIDConnectionEvent()
slug: Web/API/HIDConnectionEvent/HIDConnectionEvent
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.HIDConnectionEvent.HIDConnectionEvent
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

سازندهٔ **`HIDConnectionEvent()`** یک شیء جدید از {{domxref("HIDConnectionEvent")}} می‌سازد. معمولاً از این سازنده استفاده نمی‌شود، زیرا رویدادها هنگام تغییر وضعیت اتصال دستگاه ساخته می‌شوند.

## نحو

```js-nolint
new HIDConnectionEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای که نام رویداد را مشخص می‌کند. این مقدار به بزرگی و کوچکی حروف حساس است و مرورگرها آن را روی `connect` یا `disconnect` تنظیم می‌کنند.
- `options`
  - : شیئی که، _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `device`
      - : نمونهٔ {{domxref("HIDDevice")}} که نشان‌دهندهٔ دستگاهی است که متصل یا قطع شده است.

### مقدار بازگشتی

یک شیء جدید از {{domxref("HIDConnectionEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}