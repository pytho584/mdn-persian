---
title: "LockManager: request() method"
short-title: request()
slug: Web/API/LockManager/request
page-type: web-api-instance-method
browser-compat: api.LockManager.request
---

{{APIRef("Web Locks API")}}{{securecontext_header}} {{AvailableInWorkers}}

متد **`request()`** از رابط {{domxref("LockManager")}} یک شی {{domxref('Lock')}} را با پارامترهایی که نام و ویژگی‌های آن را مشخص می‌کنند درخواست می‌کند. `Lock` درخواست‌شده به یک callback ارسال می‌شود، در حالی که خود تابع یک {{jsxref('Promise')}} برمی‌گرداند که پس از آزاد شدن قفل، با نتیجه callback حل (resolve) می‌شود (یا reject می‌شود)، یا اگر درخواست لغو شود، reject می‌شود.

ویژگی `mode` پارامتر `options` می‌تواند `"exclusive"` یا `"shared"` باشد.

هنگامی‌که قفل باید تنها توسط یک نمونه از کد در یک زمان نگه داشته شود، یک قفل `"exclusive"` درخواست کنید. این برای کد در تب‌ها و workers اعمال می‌شود. از این برای نمایش دسترسی متقابل انحصاری (mutually exclusive) به یک منبع استفاده کنید. وقتی یک قفل `"exclusive"` برای یک نام مشخص نگه داشته شده است، هیچ قفل دیگری با همان نام نمی‌تواند نگه داشته شود.

هنگامی‌که چندین نمونه از کد می‌توانند دسترسی به یک منبع را به اشتراک بگذارند، یک قفل `"shared"` درخواست کنید. وقتی یک قفل `"shared"` برای یک نام مشخص نگه داشته شده است، قفل‌های `"shared"` دیگری با همان نام می‌توانند اعطا شوند، اما هیچ قفل `"exclusive"` با آن نام نمی‌تواند نگه داشته یا اعطا شود.

این الگوی قفل shared/exclusive در معماری تراکنش‌های پایگاه داده رایج است، به عنوان مثال برای اجازه دادن به چندین خواننده هم‌زمان (هر کدام یک قفل `"shared"` درخواست می‌کنند) اما تنها یک نویسنده (یک قفل `"exclusive"`). این به عنوان الگوی readers-writer شناخته می‌شود. در [API IndexedDB](/en-US/docs/Web/API/IndexedDB_API)، این به صورت تراکنش‌های `"readonly"` و `"readwrite"` با همان معناشناسی ارائه شده است.

## Syntax

```js-nolint
request(name, callback)
request(name, options, callback)
```

### Parameters

- `name`
  - : یک شناسه برای قفلی که می‌خواهید درخواست کنید.

- `options` {{optional_inline}}
  - : یک شی که ویژگی‌های قفلی که می‌خواهید ایجاد کنید را توصیف می‌کند. مقادیر معتبر عبارتند از:
    - `mode` {{optional_inline}}
      - : یا `"exclusive"` یا `"shared"`. مقدار پیش‌فرض `"exclusive"` است.

    - `ifAvailable` {{optional_inline}}
      - : اگر `true` باشد، درخواست قفل تنها در صورتی اعطا می‌شود که از قبل نگه داشته نشده باشد. اگر قابل اعطا نباشد، callback با `null` به جای یک نمونه `Lock` فراخوانی می‌شود. مقدار پیش‌فرض `false` است.

    - `steal` {{optional_inline}}
      - : اگر `true` باشد، هر قفل نگه‌داشته شده با همان نام آزاد می‌شود و درخواست اعطا می‌شود و از هر درخواست صف‌بندی شده برای آن پیشی می‌گیرد. مقدار پیش‌فرض `false` است.

        > [!WARNING] با احتیاط استفاده کنید! کدی که قبلاً درون قفل در حال اجرا بود به کار خود ادامه می‌دهد و ممکن است با کدی که اکنون قفل را در اختیار دارد تداخل کند.

    - `signal` {{optional_inline}}
      - : یک {{domxref("AbortSignal")}} (ویژگی {{domxref("AbortController.signal", "signal")}} یک {{domxref("AbortController")}}); اگر مشخص شده باشد و {{domxref("AbortController")}} لغو (abort) شود، درخواست قفل در صورت عدم اعطا شدن، رها می‌شود.

- `callback`
  - : متدی که هنگام اعطای قفل فراخوانی می‌شود. قفل به طور خودکار زمانی که callback باز می‌گردد (یا یک استثنا پرتاب می‌شود) آزاد می‌شود. معمولاً callback یک تابع ناهمگام (async) است که باعث می‌شود قفل تنها زمانی آزاد شود که تابع ناهمگام کاملاً به پایان رسیده باشد.

### Return value

یک {{jsxref('Promise')}} که پس از آزاد شدن قفل با نتیجه callback حل می‌شود (یا reject می‌شود)، یا اگر درخواست لغو شود، reject می‌شود.

### Exceptions

این متد ممکن است یک Promise رد شده با یک {{domxref("DOMException")}} از یکی از انواع زیر بازگرداند:

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر سند محیط به طور کامل فعال نباشد پرتاب می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر نتوان یک مدیر قفل برای محیط فعلی به دست آورد پرتاب می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر `name` با خط تیره (`-`) شروع شود، هر دو گزینه `steal` و `ifAvailable` `true` باشند، یا اگر گزینه `signal` وجود داشته باشد و _یا_ گزینه `steal` یا `ifAvailable` `true` باشد، پرتاب می‌شود.
- `AbortError` {{domxref("DOMException")}}
  - : اگر گزینه `signal` وجود داشته باشد و لغو شود پرتاب می‌شود.

## Examples

### General Example

مثال زیر استفاده پایه از متد `request()` را با یک تابع ناهمگام به عنوان callback نشان می‌دهد. پس از فراخوانی callback، هیچ کد در حال اجرای دیگری در این origin نمی‌تواند `my_resource` را تا زمانی که callback بازگردد، نگه دارد.

```js
await navigator.locks.request("my_resource", async (lock) => {
  // The lock was granted.
});
```

### `mode` example

مثال زیر نحوه استفاده از گزینه `mode` را برای خوانندگان و نویسندگان نشان می‌دهد. توجه کنید که هر دو تابع از یک قفل به نام `my_resource` استفاده می‌کنند. `doRead()` یک قفل در حالت `'shared'` درخواست می‌کند به این معنی که چندین فراخوانی ممکن است به طور هم‌زمان در میان event handlerهای مختلف، تب‌ها یا workers رخ دهد.

```js
async function doRead() {
  await navigator.locks.request(
    "my_resource",
    { mode: "shared" },
    async (lock) => {
      // Read code here.
    },
  );
}
```

تابع `doWrite()` از همان قفل اما در حالت `'exclusive'` استفاده می‌کند که فراخوانی `request()` در `doRead()` را تا زمانی که عملیات نوشتن کامل شود به تأخیر می‌اندازد. این در میان event handlerها، تب‌ها یا workers اعمال می‌شود.

```js
async function doWrite() {
  await navigator.locks.request(
    "my_resource",
    { mode: "exclusive" },
    async (lock) => {
      // Write code here.
    },
  );
}
```

### `ifAvailable` example

برای گرفتن یک قفل تنها در صورتی که از قبل نگه داشته نشده باشد، از گزینه `ifAvailable` استفاده کنید. در این تابع `await` به این معنی است که متد تا زمانی که callback کامل نشود بازنمی‌گردد. از آنجایی که قفل تنها در صورت موجود بودن اعطا می‌شود، این فراخوانی از نیاز به انتظار برای آزاد شدن قفل در جای دیگر جلوگیری می‌کند.

```js
await navigator.locks.request(
  "my_resource",
  { ifAvailable: true },
  async (lock) => {
    if (!lock) {
      // The lock was not granted - get out fast.
      return;
    }

    // The lock was granted, and no other running code in this origin is holding
    // the 'my_res_lock' lock until this returns.
  },
);
```

### `signal` example

برای انتظار برای یک قفل فقط برای مدت کوتاه، از گزینه `signal` استفاده کنید.

```js
const controller = new AbortController();
// Wait at most 200ms.
setTimeout(() => controller.abort(), 200);

try {
  await navigator.locks.request(
    "my_resource",
    { signal: controller.signal },
    async (lock) => {
      // The lock was acquired!
    },
  );
} catch (ex) {
  if (ex.name === "AbortError") {
    // The request aborted before it could be granted.
  }
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}