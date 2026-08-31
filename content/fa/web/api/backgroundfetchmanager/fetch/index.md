---
title: "BackgroundFetchManager: fetch() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchManager/fetch"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchManager: fetch() method"
short-title: fetch()
slug: Web/API/BackgroundFetchManager/fetch
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BackgroundFetchManager.fetch
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

**`fetch()`** متد از رابط {{domxref("BackgroundFetchManager")}} یک عملیات واکشی پس‌زمینه را آغاز می‌کند، با دادن یک یا چند URL یا شیء {{domxref("Request")}}.

## نحو (Syntax)

```js-nolint
fetch(id, requests)
fetch(id, requests, options)
```

### پارامترها

- `id`
  - : یک شناسه تعریف‌شده توسط توسعه‌دهنده که می‌تواند به سایر متدها منتقل شود تا {{domxref("BackgroundFetchRegistration")}} مربوط به این عملیات بازیابی شود.
- `requests`
  - : یک شیء `RequestInfo` یا آرایه‌ای از اشیاء `RequestInfo`.

    هر شیء `RequestInfo` یک شیء {{domxref("Request")}} یا یک رشته است که به عنوان آرگومان `input` به سازنده {{domxref("Request.Request()", "Request()")}} داده می‌شود.

- `options` {{optional_inline}}
  - : یک شیء که برای سفارشی‌سازی گفتگوی پیشرفت واکشی که مرورگر به کاربر نشان می‌دهد استفاده می‌شود. دارای ویژگی‌های زیر است:
    - `title` {{optional_inline}}
      - : رشته‌ای که به عنوان عنوان گفتگوی پیشرفت استفاده می‌شود.
    - `icons` {{optional_inline}}
      - : آرایه‌ای از اشیاء که هر کدام نمادی را نشان می‌دهند که مرورگر ممکن است برای گفتگوی پیشرفت استفاده کند. هر شیء دارای ویژگی‌های زیر است:
        - `src`
          - : رشته‌ای که URL فایل آیکون را نشان می‌دهد.
        - `sizes` {{optional_inline}}
          - : رشته‌ای که اندازه‌های تصویر را نشان می‌دهد، با استفاده از همان نحو ویژگی `sizes` عنصر {{HTMLElement("link")}} بیان می‌شود.
        - `type` {{optional_inline}}
          - : رشته‌ای که نوع {{Glossary("MIME")}} آیکون را نشان می‌دهد.
        - `label` {{optional_inline}}
          - : رشته‌ای که نام قابل دسترس آیکون را نشان می‌دهد.
    - `downloadTotal` {{optional_inline}}
      - : عددی که اندازه کل دانلود تخمینی را بر حسب بایت برای عملیات واکشی نشان می‌دهد. این برای نشان دادن اندازه دانلود به کاربر و نمایش پیشرفت دانلود استفاده می‌شود.

        به محض اینکه اندازه کل دانلود از `downloadTotal` فراتر رفت، واکشی لغو می‌شود.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک شیء {{domxref("BackgroundFetchRegistration")}} حل می‌شود.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر درخواستی ارائه نشود، اگر حالت یک درخواست `no-cors` باشد، اگر هیچ سرویس‌کارگری وجود نداشته باشد، اگر درخواستی با `id` درخواستی از قبل وجود داشته باشد، یا اگر درخواست شکست بخورد، مطرح می‌شود.
- `AbortError` {{domxref("DOMException")}}
  - : نشان می‌دهد که واکشی لغو شده است.
- `NotAllowedError` {{domxref("DOMException")}}
  - : نشان می‌دهد که مجوز کاربر برای انجام واکشی‌های پس‌زمینه داده نشده است.
- {{domxref("QuotaExceededError")}}
  - : اگر ذخیره‌سازی درخواست‌ها به دلیل فراتر رفتن از [سهمیه ذخیره‌سازی](/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria) مرورگر شکست بخورد، مطرح می‌شود.

## مثال‌ها

مثال زیر نحوه استفاده از `fetch()` را برای شروع یک عملیات واکشی پس‌زمینه نشان می‌دهد. با یک {{domxref('ServiceWorker', 'سرویس‌کارگر', "", "nocode")}} فعال، از ویژگی {{domxref('ServiceWorkerRegistration.backgroundFetch')}} برای دسترسی به شیء `BackgroundFetchManager` و فراخوانی متد `fetch()` آن استفاده کنید.

```js
navigator.serviceWorker.ready.then(async (swReg) => {
  const bgFetch = await swReg.backgroundFetch.fetch(
    "my-fetch",
    ["/ep-5.mp3", "ep-5-artwork.jpg"],
    {
      title: "Episode 5: Interesting things.",
      icons: [
        {
          sizes: "300x300",
          src: "/ep-5-icon.png",
          type: "image/png",
          label: "Downloading a show",
        },
      ],
      downloadTotal: 60 * 1024 * 1024,
    },
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}