---
title: "NavigationPreloadManager: getState() method"
---

---
title: "NavigationPreloadManager: getState() method"
short-title: getState()
slug: Web/API/NavigationPreloadManager/getState
page-type: web-api-instance-method
browser-compat: api.NavigationPreloadManager.getState
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`getState()`** از رابط {{domxref("NavigationPreloadManager")}} یک {{jsxref("Promise")}} برمی‌گرداند که به یک شیء resolve می‌شود. ویژگی‌های این شیء نشان می‌دهند که آیا پیش‌بارگذاری فعال است و چه مقداری در هدر HTTP {{HTTPHeader("Service-Worker-Navigation-Preload")}} ارسال خواهد شد.

## نحو

```js-nolint
getState()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک شیء شامل ویژگی‌های زیر resolve می‌شود:

- `enabled`
  - : اگر پیش‌بارگذاری فعال باشد، `true` و در غیر این صورت `false`.
- `headerValue`
  - : رشته‌ای حاوی مقداری است که هنگام یک فراخوانی {{domxref("Window/fetch", "fetch()")}} در حالت پیش‌بارگذاری، در هدر HTTP `Service-Worker-Navigation-Preload` ارسال می‌شود. این مقدار به‌طور پیش‌فرض `true` است، مگر اینکه با استفاده از {{domxref("NavigationPreloadManager.setHeaderValue()")}} تغییر کرده باشد.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : هیچ worker فعالی با ثبتی (registration) که این {{domxref("NavigationPreloadManager")}} به آن تعلق دارد، مرتبط نیست.

## مثال‌ها

کد زیر درخواست وضعیت فعلی را نشان می‌دهد؛ این درخواست پس از آماده‌شدن service worker انجام می‌شود.

```js
navigator.serviceWorker.ready
  .then((registration) => registration.navigationPreload.getState())
  .then((state) => {
    console.log(state.enabled); // boolean
    console.log(state.headerValue); // string
  })
  .catch((e) =>
    console.error(`NavigationPreloadManager not supported: ${e.message}`),
  );
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}