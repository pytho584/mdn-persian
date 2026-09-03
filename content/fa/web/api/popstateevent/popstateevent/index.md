---
title: "PopStateEvent: PopStateEvent() constructor"
short-title: PopStateEvent()
slug: Web/API/PopStateEvent/PopStateEvent
page-type: web-api-constructor
browser-compat: api.PopStateEvent.PopStateEvent
---

{{APIRef("History API")}}

سازندهٔ **`PopStateEvent()`** یک شیء {{domxref("PopStateEvent")}} جدید می‌سازد.

> [!NOTE]
> توسعه‌دهندگان وب معمولاً نیازی به فراخوانی این سازنده ندارند، زیرا مرورگر هنگام فعال‌سازی رویدادهای {{domxref("Window/popstate_event", "popstate")}} این اشیاء را به‌صورت خودکار می‌سازد.

## Syntax

```js-nolint
new PopStateEvent(type, options)
```

### Parameters

- `type`
  - : رشته‌ای است که نام رویداد را مشخص می‌کند. این مقدار به حروف بزرگ و کوچک حساس است و مرورگر آن را روی `popstate` تنظیم می‌کند.
- `options` {{optional_inline}}
  - : شیءایی که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، ویژگی زیر را دارد:
    - `state` {{optional_inline}}
      - : شیءایی است که حالت (state) را نشان می‌دهد. در عمل، این مقدار همان مقداری است که با فراخوانی {{domxref("history.pushState()")}} یا {{domxref("history.replaceState()")}} ارائه شده است. اگر تنظیم نشود، پیش‌فرض آن `null` است.

### Return value

یک شیء {{domxref("PopStateEvent")}} جدید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("history.pushState()")}}
- {{domxref("history.replaceState()")}}
- رویداد {{domxref("Window/popstate_event", "popstate")}}