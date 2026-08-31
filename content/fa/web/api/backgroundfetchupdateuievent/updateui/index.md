---
title: "BackgroundFetchUpdateUIEvent: updateUI() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchUpdateUIEvent/updateUI"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchUpdateUIEvent: updateUI() method"
short-title: updateUI()
slug: Web/API/BackgroundFetchUpdateUIEvent/updateUI
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BackgroundFetchUpdateUIEvent.updateUI
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

متد **`updateUI()`** از رابط {{domxref("BackgroundFetchUpdateUIEvent")}} عنوان و آیکون را در رابط کاربری به‌روزرسانی می‌کند تا وضعیت یک واکشی پس‌زمینه را نمایش دهد.

این متد فقط یک بار می‌تواند اجرا شود تا کاربر را در صورت موفقیت یا شکست واکشی مطلع کند.

## نحو

```js-nolint
updateUI()
updateUI(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : شیئی شامل هر یک از موارد زیر:
    - `icons` {{optional_inline}}
      - : فهرستی از یک یا چند منبع تصویر، شامل آیکون‌ها برای استفاده در رابط کاربری. یک منبع تصویر شیئی است شامل:
        - `src`
          - : یک رشته که آدرس URL یک تصویر است.
        - `sizes` {{optional_inline}}
          - : یک رشته که معادل ویژگی `sizes` عنصر {{HTMLElement("link")}} است.
        - `type` {{optional_inline}}
          - : یک رشته حاوی نوع MIME تصویر.
        - `label` {{optional_inline}}
          - : یک رشته که نامی برای تصویر مرتبط فراهم می‌کند.

    - `title` {{optional_inline}}
      - : یک رشته حاوی عنوان جدید رابط کاربری.

### مقدار بازگشتی

یک {{jsxref("Promise")}}.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر هر یک از موارد زیر درست باشد پرتاب می‌شود:
    - ویژگی {{domxref("Event.isTrusted","isTrusted")}} برابر `false` باشد.
    - پرچم به‌روزرسانی رابط کاربری {{domxref("BackgroundFetchUpdateUIEvent")}} قبلاً تنظیم شده باشد، که نشان می‌دهد متد `updateUI()` قبلاً فراخوانی شده است.
    - {{domxref("BackgroundFetchUpdateUIEvent")}} فعال نباشد.

## مثال‌ها

مثال زیر نحوه به‌روزرسانی رابط کاربری با یک عنوان و آیکون تصویر در صورت موفقیت واکشی را نشان می‌دهد.

```js
addEventListener("backgroundfetchsuccess", (event) => {
  event.updateUI({
    title: "Episode 5 ready to listen!",
    icon: {
      src: "path/to/success.ico",
      sizes: "16x16 32x32 64x64",
    },
  });
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}