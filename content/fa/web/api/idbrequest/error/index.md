---
title: "IDBRequest: error property"
short-title: error
slug: Web/API/IDBRequest/error
page-type: web-api-instance-property
browser-compat: api.IDBRequest.error
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

خاصیت فقط‑خواندنی **`error`** از رابط {{domxref("IDBRequest")}}، خطای رخ‌داده در صورت عدم موفقیت درخواست را بازمی‌گرداند.

## مقدار

یک {{domxref("DOMException")}} یا `null` در صورت عدم وجود خطا. شیء استثنا بسته به علت خطا، یکی از نام‌های زیر را خواهد داشت.

این خطاها ناهمزمان هستند، به این معنی که نمی‌توان با [`try...catch`](/en-US/docs/Web/JavaScript/Reference/Statements/try...catch) آن‌ها را مدیریت کرد. با این حال، اگر یک `IDBRequest` یک کنترل‌کننده رویداد {{domxref("IDBRequest.error_event", "error")}} داشته باشد، می‌توانید با پرس‌وجوی خاصیت `error` درخواست از طریق شیء رویداد، این خطاها را بررسی کنید، برای مثال [`event.target.error.name`](/en-US/docs/Web/API/DOMException/name) یا [`event.target.error.message`](/en-US/docs/Web/API/DOMException/message).

- `AbortError`
  - : اگر تراکنش را لغو کنید، تمام درخواست‌های در حال اجرا این خطا را دریافت می‌کنند.
- `ConstraintError`
  - : اگر داده‌ای را وارد کنید که با یک محدودیت در هنگام پر کردن ذخیره‌گاه‌ها مطابقت ندارد، این خطا دریافت می‌شود. برای مثال، اگر سعی کنید کلید جدیدی اضافه کنید که از قبل در ذخیره‌گاه وجود دارد، این خطا را خواهید گرفت.
- `NotReadableError`
  - : برای خطاهای خواندن غیرقابل بازیابی دریافت می‌شود. به طور خاص، این خطا نشان می‌دهد که رکورد در پایگاه داده وجود دارد، اما مقدار قابل بازیابی نیست. برای جزئیات بیشتر به [خطاهای خواندن موقت و غیرقابل بازیابی](#transient_and_unrecoverable_read_errors) در زیر مراجعه کنید.
- {{domxref("QuotaExceededError")}}
  - : اگر برنامه از سهمیه دیسک خود استفاده کند، این خطا دریافت می‌شود. در برخی موارد، مرورگرها از کاربر فضای بیشتری درخواست می‌کنند و اگر درخواست رد شود، خطا دریافت می‌شود. در موارد دیگر، مرورگر از اکتشافی برای تعیین اینکه آیا می‌توان فضای بیشتری اختصاص داد استفاده می‌کند.
- `UnknownError`
  - : برای خطاهای خواندن موقت، از جمله خطاهای عمومی ورودی/خروجی دیسک دریافت می‌شود. برای جزئیات بیشتر به [خطاهای خواندن موقت و غیرقابل بازیابی](#transient_and_unrecoverable_read_errors) در زیر مراجعه کنید.
- `VersionError`
  - : اگر سعی کنید پایگاه داده‌ای را با نسخه‌ای پایین‌تر از نسخه فعلی باز کنید، این خطا دریافت می‌شود.

### خطاهای خواندن موقت و غیرقابل بازیابی

خطاهای خواندن زمانی رخ می‌دهند که IndexedDB مقادیری را ذخیره می‌کند و سپس در خواندن آن مقادیر ناموفق است، حتی اگر رکوردهای مرتبط همچنان در پایگاه داده باشند.

خطاهای خواندن می‌توانند از دو نوع باشند — **موقت (transient)** یا **غیرقابل بازیابی (unrecoverable)** :

خطاهای خواندن موقت توسط نوع `UnknownError` نشان داده می‌شوند و معمولاً ناشی از کمبود حافظه هستند. این نباید برای پایگاه‌های داده کوچک مشکلی ایجاد کند. برای جلوگیری از موقعیت‌های کمبود حافظه در پایگاه‌های داده بزرگ، سعی کنید دسترسی به پایگاه داده را به گونه‌ای تقسیم کنید که فقط رکوردهای مورد نیاز خود را در هر زمان بارگذاری کنید، به عنوان مثال با استفاده از [محدوده‌های کلید](/en-US/docs/Web/API/IDBKeyRange) خاص مربوط به جستجوی کاربر یا یک مکانیسم صفحه‌بندی. اگر با خطای کمبود حافظه مواجه شدید، ممکن است از کاربر خواسته شود برنامه‌های دیگر را ببندد تا فضای حافظه در سطح سیستم‌عامل آزاد شود.

خطاهای خواندن غیرقابل بازیابی توسط نوع `NotReadableError` نشان داده می‌شوند و ناشی از حذف فایل‌های منبع هستند.

برای مثال، برخی مرورگرها مقادیر بزرگ (مانند blobs فایل صوتی برای یک برنامه پادکست آفلاین) را به عنوان فایل‌های جداگانه ذخیره می‌کنند که از طریق یک مرجع ذخیره شده در پایگاه داده قابل دسترسی هستند. مشاهده شده است که این فایل‌های جداگانه ممکن است حذف شوند زیرا هنگام استفاده از برنامه‌های بازیابی فضای دیسک، به عنوان فایل‌های مبهم برای کاربران ظاهر می‌شوند و در نتیجه وقتی IndexedDB دفعه بعد دسترسی پیدا می‌کند، خطاهای خواندن غیرقابل بازیابی رخ می‌دهد.

اقدامات اصلاحی ممکن برای خطاهای خواندن غیرقابل بازیابی می‌تواند شامل اطلاع‌رسانی به کاربر، حذف ورودی از پایگاه داده و سپس تلاش برای دریافت مجدد داده از سرور باشد.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که سعی شود به خاصیت دسترسی پیدا شود در حالی که درخواست کامل نشده است و بنابراین خطا در دسترس نیست.

## مثال‌ها

مثال زیر یک عنوان رکورد مشخص را درخواست می‌کند، `onsuccess` رکورد مرتبط را از {{domxref("IDBObjectStore")}} (که به صورت `objectStoreTitleRequest.result` در دسترس است) دریافت می‌کند، یک خاصیت از رکورد را به‌روزرسانی می‌کند، و سپس رکورد به‌روزرسانی شده را دوباره در object store قرار می‌دهد. همچنین در پایین یک تابع `onerror` وجود دارد که اگر درخواست ناموفق باشد، خطا را گزارش می‌کند. برای یک مثال کامل کار، برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ما را ببینید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
const title = "Walk dog";

// Open up a transaction as usual
const objectStore = db
  .transaction(["toDoList"], "readwrite")
  .objectStore("toDoList");

// Get the to-do list with the specified title
const objectStoreTitleRequest = objectStore.get(title);

objectStoreTitleRequest.onsuccess = () => {
  // Grab the data object returned as the result
  const data = objectStoreTitleRequest.result;

  // Update the notified value in the object to "yes"
  data.notified = "yes";

  // Create another request that inserts the item
  // back into the database
  const updateTitleRequest = objectStore.put(data);

  // When this new request succeeds, run the displayData()
  // function again to update the display
  updateTitleRequest.onsuccess = () => {
    displayData();
  };
};

objectStoreTitleRequest.onerror = () => {
  // If an error occurs with the request, log what it is
  console.log(
    `There has been an error with retrieving your data:
    ${objectStoreTitleRequest.error.name}: ${objectStoreTitleRequest.error.message}`,
  );
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).