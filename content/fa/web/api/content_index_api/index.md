---
title: Content Index API
slug: Web/API/Content_Index_API
page-type: web-api-overview
status:
  - experimental
browser-compat:
  - api.ContentIndex
  - api.ServiceWorkerRegistration.index
spec-urls: https://wicg.github.io/content-index/spec/
---

{{DefaultAPISidebar("Content Index API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

**Content Index API** به توسعه‌دهندگان اجازه می‌دهد محتوای آفلاین‌فعال خود را با مرورگر ثبت کنند.

## مفاهیم و کاربرد

در حال حاضر، محتوای وب آفلاین به‌راحتی توسط کاربران قابل کشف نیست. نمایه‌سازی محتوا (Content Indexing) به توسعه‌دهندگان امکان می‌دهد تا مرورگر را از محتوای آفلاین خاص خود مطلع کنند. این کار به کاربران اجازه می‌دهد محتوای موجود را کشف و مشاهده کنند و در عین حال به توسعه‌دهندگان توانایی افزودن و مدیریت این محتوا را می‌دهد. به عنوان مثال، یک وب‌سایت خبری می‌تواند آخرین مقاله‌ها را در پس‌زمینه از قبل دریافت کند، یا یک برنامه‌ی استریم محتوا می‌تواند محتوای دانلود شده را ثبت کند.

Content Index API یک افزونه بر [سرویس‌ورکرها](/en-US/docs/Web/API/Service_Worker_API) است که به توسعه‌دهندگان اجازه می‌دهد تا URLها و فراداده‌ی صفحات ذخیره‌شده را در محدوده‌ی سرویس‌ورکر جاری اضافه کنند. سپس مرورگر می‌تواند از این ورودی‌ها برای نمایش خواندن آفلاین به کاربر استفاده کند. به عنوان توسعه‌دهنده، شما نیز می‌توانید این ورودی‌ها را در برنامه‌ی خود نمایش دهید.

ورودی‌های نمایه‌شده به صورت خودکار منقضی نمی‌شوند. بهتر است یک رابط کاربری برای پاک‌کردن ورودی‌ها ارائه دهید یا به صورت دوره‌ای ورودی‌های قدیمی‌تر را حذف کنید.

> [!NOTE]
> این API از نمایه‌سازی URLهایی که به اسناد HTML اشاره می‌کنند پشتیبانی می‌کند. برای مثال، URL یک فایل رسانه‌ای ذخیره‌شده را نمی‌توان به طور مستقیم نمایه‌سازی کرد. در عوض، باید URL صفحه‌ای را ارائه دهید که رسانه را نمایش می‌دهد و به صورت آفلاین کار می‌کند.

## رابط‌ها

- {{domxref("ContentIndex")}} {{Experimental_Inline}}
  - : امکان ثبت محتوای قابل دسترسی به صورت آفلاین را فراهم می‌کند.
- {{domxref("ContentIndexEvent")}} {{Experimental_Inline}}
  - : شیء مورد استفاده برای نمایش رویداد {{domxref("ServiceWorkerGlobalScope.contentdelete_event", "contentdelete")}} را تعریف می‌کند.

### افزونه‌های رابط‌های دیگر

افزونه‌های زیر در مشخصات Content Index API به {{domxref('ServiceWorker')}} اضافه شده‌اند تا نقطه‌ی ورودی برای استفاده از نمایه‌سازی محتوا فراهم کنند.

- {{domxref("ServiceWorkerRegistration.index")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک مرجع به رابط {{domxref("ContentIndex")}} برای نمایه‌سازی صفحات ذخیره‌شده برمی‌گرداند.
- {{domxref("ServiceWorkerGlobalScope.contentdelete_event", "contentdelete")}} event {{Experimental_Inline}}
  - : زمانی که محتوا توسط عامل کاربر حذف می‌شود، رخ می‌دهد.

## مثال‌ها

همه‌ی مثال‌های زیر فرض می‌کنند که یک سرویس‌ورکر ثبت شده است. برای اطلاعات بیشتر به [Service Worker API](/en-US/docs/Web/API/Service_Worker_API) مراجعه کنید.

### تشخیص قابلیت و دسترسی به رابط

در اینجا یک مرجع به {{domxref('ServiceWorkerRegistration')}} می‌گیریم و سپس ویژگی `index` را بررسی می‌کنیم که به ما دسترسی به رابط نمایه‌ی محتوا می‌دهد.

```js
// reference registration
const registration = await navigator.serviceWorker.ready;

// feature detection
if ("index" in registration) {
  // Content Index API functionality
  const contentIndex = registration.index;
}
```

### افزودن به نمایه‌ی محتوا

در اینجا یک آیتم را در قالب صحیح تعریف می‌کنیم و یک تابع ناهمگام می‌سازیم که از متد {{domxref('ContentIndex.add','add()')}} برای ثبت آن در نمایه‌ی محتوا استفاده می‌کند.

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

### بازیابی آیتم‌ها در نمایه‌ی فعلی

مثال زیر یک تابع ناهمگام را نشان می‌دهد که آیتم‌های موجود در نمایه‌ی محتوا را بازیابی می‌کند و روی هر ورودی تکرار می‌کند تا فهرستی برای رابط کاربری بسازد.

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

### لغو ثبت محتوای نمایه‌شده

در زیر یک تابع ناهمگام است که یک آیتم را از نمایه‌ی محتوا حذف می‌کند.

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

همه‌ی متدهای بالا در محدوده‌ی [سرویس‌ورکر](/en-US/docs/Web/API/ServiceWorker) در دسترس هستند. این متدها از طریق ویژگی {{domxref('WorkerGlobalScope.self')}} قابل دسترسی‌اند:

```js
// service worker script

self.registration.index.add(item);

self.registration.index.delete(item.id);

const contentIndexItems = self.registration.index.getAll();
```

### رویداد contentdelete

هنگامی که یک آیتم از رابط کاربری عامل کاربر حذف می‌شود، یک رویداد `contentdelete` توسط سرویس‌ورکر دریافت می‌شود.

```js
self.addEventListener("contentdelete", (event) => {
  console.log(event.id);

  // logs content index id, which can then be used to determine what content to delete from your cache
});
```

رویداد {{domxref('ServiceWorkerGlobalScope.contentdelete_event', "contentdelete")}} تنها زمانی رخ می‌دهد که حذف به دلیل تعامل با رابط کاربری داخلی مرورگر باشد. این رویداد هنگامی که متد {{domxref('ContentIndex.delete()')}} فراخوانی می‌شود، رخ نمی‌دهد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [یک مقاله‌ی مقدماتی درباره‌ی Content Index API](https://developer.chrome.com/docs/capabilities/web-apis/content-indexing-api)
- [Service Worker API، همراه با اطلاعاتی درباره‌ی Cache و CacheStorage](/en-US/docs/Web/API/Service_Worker_API)