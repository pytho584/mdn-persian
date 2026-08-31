---
title: "ContentIndex: getAll() method"
short-title: getAll()
slug: Web/API/ContentIndex/getAll
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.ContentIndex.getAll
---

{{APIRef("Content Index API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

متد **`getAll()`** در رابط {{domxref("ContentIndex")}} یک {{jsxref('Promise')}} برمی‌گرداند که با فهرست قابل پیمایشی از ورودی‌های فهرست محتوا حل می‌شود.

## نحو (Syntax)

```js-nolint
getAll()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} برمی‌گرداند که با یک {{jsxref('Array')}} از موارد `contentDescription` حل می‌شود.

- `contentDescription`
  - : هر مورد بازگشتی یک {{jsxref('Object')}} است که داده‌های زیر را شامل می‌شود:
    - `id`
      - : یک شناسه یکتای {{jsxref('String')}}.
    - `title`
      - : عنوان {{jsxref('String')}} آیتم. در فهرست‌های قابل مشاهده برای کاربر از محتوا استفاده می‌شود.
    - `description`
      - : توضیح {{jsxref('String')}} آیتم. در فهرست‌های قابل مشاهده برای کاربر از محتوا استفاده می‌شود.
    - `url`
      - : یک {{jsxref('String')}} شامل URL سند HTML متناظر. باید در محدوده [service worker](/en-US/docs/Web/API/ServiceWorker) فعلی باشد.
    - `category` {{Optional_Inline}}
      - : یک {{jsxref('String')}} که دسته محتوا را تعریف می‌کند. می‌تواند یکی از موارد زیر باشد:
        - `''` یک {{jsxref('String')}} خالی، که مقدار پیش‌فرض است.
        - `homepage`
        - `article`
        - `video`
        - `audio`

    - `icons` {{Optional_Inline}}
      - : یک {{jsxref('Array')}} از منابع تصویری، که به صورت {{jsxref('Object')}} با داده‌های زیر تعریف شده‌اند:
        - `src`
          - : یک {{jsxref('String')}} URL از تصویر منبع.
        - `sizes` {{Optional_Inline}}
          - : یک {{jsxref('String')}} نمایش‌دهنده اندازه تصویر.
        - `type` {{Optional_Inline}}
          - : {{Glossary("MIME type")}} تصویر.
        - `label` {{Optional_Inline}}
          - : رشته‌ای که نام قابل دسترس آیکون را نشان می‌دهد.

### استثناها

هیچ استثنایی پرتاب نمی‌شود. اگر هیچ موردی در فهرست محتوا وجود نداشته باشد، یک {{jsxref('Array')}} خالی برگردانده می‌شود.

## مثال‌ها

مثال زیر یک تابع ناهمگام را نشان می‌دهد که موارد موجود در [فهرست محتوا](/en-US/docs/Web/API/Content_Index_API) را بازیابی می‌کند و روی هر ورودی پیمایش می‌کند و یک فهرست برای رابط کاربری می‌سازد.

```js
async function createReadingList() {
  // access our service worker registration
  const registration = await navigator.serviceWorker.ready;

  // get our index entries
  const entries = await registration.index.getAll();

  // create a containing element
  const readingListElem = document.createElement("div");

  // test for entries
  if (entries.length === 0) {
    // if there are no entries, display a message
    const message = document.createElement("p");
    message.innerText =
      "You currently have no articles saved for offline reading.";

    readingListElem.append(message);
  } else {
    // if entries are present, display in a list of links to the content
    const listElem = document.createElement("ul");

    for (const entry of entries) {
      const listItem = document.createElement("li");

      const anchorElem = document.createElement("a");
      anchorElem.innerText = entry.title;
      anchorElem.setAttribute("href", entry.url);

      listElem.append(listItem);
    }

    readingListElem.append(listElem);
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مقاله مقدماتی درباره Content Index API](https://developer.chrome.com/docs/capabilities/web-apis/content-indexing-api)
- [Service Worker API، همراه با اطلاعاتی درباره Cache و CacheStorage](/en-US/docs/Web/API/Service_Worker_API)