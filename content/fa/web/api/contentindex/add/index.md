---
title: "ContentIndex: add() method"
short-title: add()
slug: Web/API/ContentIndex/add
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.ContentIndex.add
---

{{APIRef("Content Index API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

متد **`add()`** از رابط {{domxref("ContentIndex")}} یک مورد را در [فهرست محتوا](/en-US/docs/Web/API/Content_Index_API) ثبت می‌کند.

## نحو

```js-nolint
add(contentDescription)
```

### پارامترها

- `contentDescription`
  - : یک {{jsxref('Object')}} شامل داده‌های زیر:
    - `id`
      - : یک شناسه منحصربه‌فرد از نوع {{jsxref('String')}}.
    - `title`
      - : یک عنوان از نوع {{jsxref('String')}} برای مورد. در لیست‌های قابل مشاهده برای کاربر از محتوا استفاده می‌شود.
    - `description`
      - : یک توضیح از نوع {{jsxref('String')}} برای مورد. در لیست‌های قابل مشاهده برای کاربر از محتوا استفاده می‌شود.
    - `url`
      - : یک {{jsxref('String')}} شامل URL سند HTML مربوطه. باید در حیطه (scope) [service worker](/en-US/docs/Web/API/ServiceWorker) جاری باشد.
    - `category` {{Optional_Inline}}
      - : یک {{jsxref('String')}} که دسته‌بندی محتوا را تعریف می‌کند. می‌تواند:
        - `''` یک {{jsxref('String')}} خالی، که پیش‌فرض است.
        - `homepage`
        - `article`
        - `video`
        - `audio`
    - `icons` {{Optional_Inline}}
      - : یک {{jsxref('Array')}} از منابع تصویر، که به صورت یک {{jsxref('Object')}} با داده‌های زیر تعریف می‌شود:
        - `src`
          - : یک URL از نوع {{jsxref('String')}} برای تصویر منبع.
        - `sizes` {{Optional_Inline}}
          - : یک نمایش از نوع {{jsxref('String')}} از اندازه تصویر.
        - `type` {{Optional_Inline}}
          - : {{Glossary("MIME type")}} تصویر.
        - `label` {{Optional_Inline}}
          - : یک رشته که نام قابل دسترس (accessible) آیکون را نشان می‌دهد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} برمی‌گرداند که با `undefined` حل می‌شود.

### استثناها

- {{jsxref("TypeError")}}
  - : این استثنا در شرایط زیر پرتاب می‌شود:
    - ثبت (registration) سرویس‌ورکر وجود ندارد یا سرویس‌ورکر شامل {{domxref('FetchEvent')}} نیست.
    - یکی از پارامترهای `id`، `title`، `description` یا `url` وجود نداشته باشد، از نوع {{jsxref('String')}} نباشد، یا یک {{jsxref('String')}} خالی باشد.
    - پارامتر `url` با {{glossary("same-origin policy")}} (خط مشی همان مبدأ) {{domxref("ServiceWorker", "سرویس‌ورکر", "", "nocode")}} مطابقت نداشته باشد.
    - یکی از موارد موجود در `icons` از نوع تصویر نباشد، یا واکشی یکی از موارد موجود در `icons` با خطای شبکه یا خطای رمزگشایی (decode) شکست بخورد.

## مثال‌ها

در اینجا یک مورد را با فرمت صحیح اعلام می‌کنیم و یک تابع ناهمگام (async) ایجاد می‌کنیم که از متد `add` برای ثبت آن در [فهرست محتوا](/en-US/docs/Web/API/Content_Index_API) استفاده می‌کند.

```js
// محتوای ما
const item = {
  id: "post-1",
  url: "/posts/amet.html",
  title: "Amet consectetur adipisicing",
  description:
    "Repellat et quia iste possimus ducimus aliquid a aut eaque nostrum.",
  icons: [
    {
      src: "/media/dark.png",
      sizes: "128x128",
      type: "image/png",
    },
  ],
  category: "article",
};

// تابع ناهمگام ما برای افزودن محتوای فهرست‌شده
async function registerContent(data) {
  const registration = await navigator.serviceWorker.ready;

  // تشخیص قابلیت Content Index
  if (!registration.index) {
    return;
  }

  // ثبت محتوا
  try {
    await registration.index.add(data);
  } catch (e) {
    console.log("Failed to register content: ", e.message);
  }
}
```

متد `add` همچنین می‌تواند در حیطه (scope) [سرویس‌ورکر](/en-US/docs/Web/API/ServiceWorker) استفاده شود.

```js
// محتوای ما
const item = {
  id: "post-1",
  url: "/posts/amet.html",
  title: "Amet consectetur adipisicing",
  description:
    "Repellat et quia iste possimus ducimus aliquid a aut eaque nostrum.",
  icons: [
    {
      src: "/media/dark.png",
      sizes: "128x128",
      type: "image/png",
    },
  ],
  category: "article",
};

self.registration.index.add(item);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [یک مقاله مقدماتی درباره Content Index API](https://developer.chrome.com/docs/capabilities/web-apis/content-indexing-api)
- [Service Worker API، همراه با اطلاعاتی درباره Cache و CacheStorage](/en-US/docs/Web/API/Service_Worker_API)