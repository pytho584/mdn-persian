---
title: "BackgroundFetchRegistration: matchAll() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchRegistration/matchAll"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchRegistration: matchAll() method"
short-title: matchAll()
slug: Web/API/BackgroundFetchRegistration/matchAll
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BackgroundFetchRegistration.matchAll
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

متد **`matchAll()`** از رابط {{domxref("BackgroundFetchRegistration")}} یک آرایه از اشیاء {{domxref("BackgroundFetchRecord")}} مطابق را برمی‌گرداند.

## Syntax

```js-nolint
matchAll()
matchAll(request)
matchAll(request,options)
```

### Parameters

- `request` {{optional_inline}}
  - : {{domxref("Request")}}ای که برای یافتن رکوردها تلاش می‌کنید.
    این می‌تواند یک شیء {{domxref("Request")}} یا یک URL باشد. اگر این پارامتر حذف شود، همه رکوردها در نتیجه گنجانده می‌شوند.
- `options` {{optional_inline}}
  - : شیءای که گزینه‌هایی را برای عملیات `match` تنظیم می‌کند. گزینه‌های موجود عبارتند از:
    - `ignoreSearch` {{optional_inline}}
      - : یک مقدار بولی که مشخص می‌کند آیا رشته query در URL نادیده گرفته شود. برای مثال، اگر روی `true` تنظیم شود، بخش `?value=bar` از `https://example.com/?value=bar` هنگام انجام تطبیق نادیده گرفته می‌شود. پیش‌فرض `false` است.
    - `ignoreMethod` {{optional_inline}}
      - : یک مقدار بولی. وقتی `true` باشد، از اعتبارسنجی متد `http` {{domxref("Request")}} در عملیات تطبیق جلوگیری می‌کند. اگر `false` (پیش‌فرض) باشد، فقط `GET` و `HEAD` مجاز هستند.
    - `ignoreVary` {{optional_inline}}
      - : یک مقدار بولی. وقتی `true` باشد، نشان می‌دهد که هدر {{HTTPHeader("Vary")}} باید نادیده گرفته شود. پیش‌فرض `false` است.

### Return value

یک {{jsxref("Promise")}} که با یک آرایه از تمام اشیاء {{domxref("BackgroundFetchRecord")}} مطابق حل می‌شود.

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر پرچم {{domxref("BackgroundFetchRegistration.recordsAvailable","recordsAvailable")}} `false` باشد، بازگردانده می‌شود و نشان می‌دهد که هیچ واکشی در حال انجام نیست.

## Examples

از `matchAll()` بدون پارامتر استفاده کنید تا تمام رکوردهای یک پس‌زمینه‌ی واکشی را برگردانید.

```js
const records = await bgFetch.matchAll();
console.log(records); // an array of BackgroundFetchRecord objects
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
```