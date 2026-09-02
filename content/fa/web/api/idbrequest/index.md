---
title: IDBRequest
slug: Web/API/IDBRequest
page-type: web-api-interface
browser-compat: api.IDBRequest
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

رابط **`IDBRequest`** از API IndexedDB دسترسی به نتایج درخواست‌های ناهمگام (asynchronous) به پایگاه‌های داده و اشیاء پایگاه داده را با استفاده از ویژگی‌های کنترل‌کننده رویداد (event handler attributes) فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه (Instance properties)

_همچنین ویژگی‌های {{domxref("EventTarget")}} را به ارث می‌برد._

- {{domxref("IDBRequest.error")}} {{ReadOnlyInline}}
  - : در صورت عدم موفقیت درخواست، یک {{domxref("DOMException")}} را برمی‌گرداند که نشان می‌دهد چه مشکلی پیش آمده است.
- {{domxref("IDBRequest.result")}} {{ReadOnlyInline}}
  - : نتیجه درخواست را برمی‌گرداند. اگر درخواست تکمیل نشده باشد، نتیجه در دسترس نیست و یک استثنای `InvalidStateError` پرتاب می‌شود.
- {{domxref("IDBRequest.source")}} {{ReadOnlyInline}}
  - : منبع درخواست، مانند یک {{domxref("IDBIndex")}} یا یک {{domxref("IDBObjectStore")}}. اگر منبعی وجود نداشته باشد (مانند هنگام فراخوانی {{domxref("IDBFactory.open")}})، مقدار `null` را برمی‌گرداند.
- {{domxref("IDBRequest.readyState")}} {{ReadOnlyInline}}
  - : وضعیت درخواست. هر درخواست در وضعیت `pending` شروع می‌شود. وضعیت زمانی به `done` تغییر می‌کند که درخواست با موفقیت تکمیل شود یا خطایی رخ دهد.
- {{domxref("IDBRequest.transaction")}} {{ReadOnlyInline}}
  - : تراکنش مربوط به درخواست. این ویژگی می‌تواند برای برخی درخواست‌ها `null` باشد، مانند درخواست‌هایی که از {{domxref("IDBFactory.open")}} برگردانده می‌شوند، مگر اینکه نیاز به ارتقا (upgrade) باشد. (شما فقط به یک پایگاه داده متصل می‌شوید، بنابراین تراکنشی برای بازگرداندن وجود ندارد.)

## روش‌های نمونه (Instance methods)

_بدون روش (method)، اما روش‌هایی را از {{domxref("EventTarget")}} به ارث می‌برد._

## رویدادها (Events)

به این رویدادها با استفاده از `addEventListener()` یا با تخصیص یک شنونده رویداد به ویژگی `oneventname` این رابط گوش دهید.

- [`error`](/en-US/docs/Web/API/IDBRequest/error_event)
  - : زمانی که یک خطا باعث شکست درخواست شود، فعال می‌شود.
- [`success`](/en-US/docs/Web/API/IDBRequest/success_event)
  - : زمانی که یک `IDBRequest` با موفقیت انجام شود، فعال می‌شود.

## توضیحات (Description)

نتایج تمام عملیات خواندن و نوشتن پایگاه داده با استفاده از یک شیء درخواست از این نوع گزارش می‌شوند.

شیء درخواست در ابتدا هیچ اطلاعاتی درباره نتیجه عملیات ندارد، اما به محض در دسترس شدن اطلاعات، یک رویداد روی درخواست فعال می‌شود و اطلاعات از طریق ویژگی‌های نمونه `IDBRequest` در دسترس قرار می‌گیرد.

تمام عملیات ناهمگام بلافاصله یک نمونه `IDBRequest` را برمی‌گردانند. هر درخواست دارای یک `readyState` است که روی وضعیت `'pending'` تنظیم شده است؛ این وضعیت وقتی درخواست تکمیل یا ناموفق شود، به `'done'` تغییر می‌کند. وقتی وضعیت `done` باشد، هر درخواست یک `result` و یک `error` برمی‌گرداند و یک رویداد روی درخواست فعال می‌شود. وقتی وضعیت همچنان `pending` است، هر تلاشی برای دسترسی به `result` یا `error` یک استثنای `InvalidStateError` را ایجاد می‌کند.

به زبان ساده، تمام روش‌های ناهمگام یک شیء درخواست را برمی‌گردانند. اگر درخواست با موفقیت تکمیل شده باشد، نتیجه از طریق ویژگی `result` در دسترس قرار می‌گیرد و یک رویداد نشان‌دهنده موفقیت در درخواست فعال می‌شود ({{domxref("IDBRequest.success_event", "success")}}). اگر در حین انجام عملیات خطایی رخ دهد، استثنا از طریق ویژگی `error` در دسترس قرار می‌گیرد و یک رویداد خطا فعال می‌شود ({{domxref("IDBRequest.error_event", "error")}}).
داده‌های موجود در `result` به عملیاتی که فراخوانی شده است بستگی دارد.

رابط {{domxref("IDBOpenDBRequest")}} از `IDBRequest` مشتق شده است.

## مثال (Example)

### استفاده پایه (Basic usage)

در قطعه کد زیر، ما یک پایگاه داده را به صورت ناهمگام باز می‌کنیم و یک درخواست انجام می‌دهیم؛ شنونده‌های رویداد برای `error` و `success` برای مدیریت موارد موفقیت و خطا گنجانده شده‌اند.
برای یک مثال کامل و کاربردی، به برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ما مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
let db;

// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

// Handle the case where there is an error opening the database
DBOpenRequest.addEventListener("error", (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Error loading database.";
});

// Handle the case where the database opens successfully
DBOpenRequest.addEventListener("success", (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database.
  db = DBOpenRequest.result;
});
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید (See also)

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها (cursors): {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).