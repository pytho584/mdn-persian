---
title: "ContentIndex"
---

---
title: ContentIndex
slug: Web/API/ContentIndex
page-type: web-api-interface
status:
  - experimental
browser-compat: api.ContentIndex
---

{{APIRef("Content Index API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

رابط **`ContentIndex`** در [Content Index API](/en-US/docs/Web/API/Content_Index_API) به توسعه‌دهندگان امکان می‌دهد محتوای فعال‌شده برای حالت آفلاین خود را در مرورگر ثبت کنند.

## ویژگی‌های نمونه

این رابط هیچ ویژگی‌ای ندارد.

## متدهای نمونه

- {{domxref('ContentIndex.add()')}} {{Experimental_Inline}}
  - : یک مورد را در [فهرست محتوا](/en-US/docs/Web/API/Content_Index_API) ثبت می‌کند.
- {{domxref('ContentIndex.delete()')}} {{Experimental_Inline}}
  - : یک مورد را از محتوای فهرست‌شدهٔ فعلی لغو ثبت می‌کند.
- {{domxref('ContentIndex.getAll()')}} {{Experimental_Inline}}
  - : یک {{jsxref('Promise')}} برمی‌گرداند که با یک فهرست قابل پیمایش (iterable) از ورودی‌های فهرست محتوا resolve می‌شود.

## نمونه‌ها

### تشخیص ویژگی (Feature detection) و دسترسی به رابط

در اینجا یک ارجاع به {{domxref('ServiceWorkerRegistration')}} می‌گیریم و سپس ویژگی `index` را بررسی می‌کنیم که به ما دسترسی به رابط فهرست محتوا را می‌دهد.

```js
// reference registration
const registration = await navigator.serviceWorker.ready;

// feature detection
if ("index" in registration) {
  // Content Index API functionality
  const contentIndex = registration.index;
}
```

### افزودن به فهرست محتوا

در اینجا یک مورد (item) را با فرمت صحیح تعریف می‌کنیم و یک تابع ناهمگام (asynchronous) می‌سازیم که از متد {{domxref('ContentIndex.add','add()')}} برای ثبت آن در [فهرست محتوا](/en-US/docs/Web/API/Content_Index_API) استفاده می‌کند.

```js
// our content
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

// our asynchronous function to add indexed content
async function registerContent(data) {
  const registration = await navigator.serviceWorker.ready;

  // feature detect Content Index
  if (!registration.index) {
    return;
  }

  // register content
  try {
    await registration.index.add(data);
  } catch (e) {
    console.log("Failed to register content: ", e.message);
  }
}
```

### دریافت موارد موجود در فهرست فعلی

مثال زیر یک تابع ناهمگام را نشان می‌دهد که موارد موجود در [فهرست محتوا](/en-US/docs/Web/API/Content_Index_API) را دریافت می‌کند، روی هر ورودی پیمایش می‌کند و فهرستی برای رابط کاربری می‌سازد.

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

### لغو ثبت محتوای فهرست‌شده

در زیر یک تابع ناهمگام آمده است که یک مورد را از [فهرست محتوا](/en-US/docs/Web/API/Content_Index_API) حذف می‌کند.

```js
async function unregisterContent(article) {
  // reference registration
  const registration = await navigator.serviceWorker.ready;

  // feature detect Content Index
  if (!registration.index) return;

  // unregister content from index
  await registration.index.delete(article.id);
}
```

همهٔ متدهای فوق در محدودهٔ [service worker](/en-US/docs/Web/API/ServiceWorker) در دسترس هستند. این متدها از طریق ویژگی {{domxref('WorkerGlobalScope.self')}} قابل دسترسی هستند:

```js
// service worker script

self.registration.index.add(item);

self.registration.index.delete(item.id);

const contentIndexItems = self.registration.index.getAll();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [یک مقالهٔ مقدماتی دربارهٔ Content Index API](https://developer.chrome.com/docs/capabilities/web-apis/content-indexing-api)
- [Service Worker API، به همراه اطلاعاتی دربارهٔ Cache و CacheStorage](/en-US/docs/Web/API/Service_Worker_API)