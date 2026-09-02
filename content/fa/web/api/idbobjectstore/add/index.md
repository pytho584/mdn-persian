---
title: "IDBObjectStore: add() method"
short-title: add()
slug: Web/API/IDBObjectStore/add
page-type: web-api-instance-method
browser-compat: api.IDBObjectStore.add
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`add()`** از رابط {{domxref("IDBObjectStore")}} یک شیء {{domxref("IDBRequest")}} را برمی‌گرداند و در یک رشته مجزا، یک [clone ساخت‌یافته](https://html.spec.whatwg.org/multipage/common-dom-interfaces.html#structured-clone) از مقدار ایجاد کرده و آن را در object store ذخیره می‌کند. این متد برای افزودن رکوردهای جدید به یک object store استفاده می‌شود.

برای تعیین اینکه عملیات add با موفقیت تکمیل شده است، علاوه بر رویداد `success` درخواست `IDBObjectStore.add`، به رویداد `complete` تراکنش نیز گوش دهید، زیرا ممکن است تراکنش پس از فعال شدن رویداد success همچنان شکست بخورد. به عبارت دیگر، رویداد success تنها زمانی فعال می‌شود که تراکنش با موفقیت در صف قرار گرفته باشد.

متد add یک متد _فقط درج_ است. اگر یک رکورد از قبل در object store با پارامتر `key` به عنوان کلید آن وجود داشته باشد، یک رویداد خطای `ConstraintError` روی شیء درخواست برگشتی فعال می‌شود. برای به‌روزرسانی رکوردهای موجود، باید از متد {{domxref("IDBObjectStore.put")}} استفاده کنید.

## Syntax

```js-nolint
add(value)
add(value, key)
```

### Parameters

- `value`
  - : مقداری که باید ذخیره شود.
- `key` {{optional_inline}}
  - : کلیدی که برای شناسایی رکورد استفاده می‌شود. اگر مشخص نشود، به null تبدیل می‌شود.

### Return value

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مرتبط با این عملیات روی آن فعال می‌شوند. اگر عملیات موفقیت‌آمیز باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست، کلید رکورد جدید خواهد بود.

### Exceptions

این متد ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر را پرتاب کند:

- `ReadOnlyError` {{domxref("DOMException")}}
  - : اگر تراکنش مرتبط با این عملیات در حالت فقط خواندنی (<a href="/en-US/docs/Web/API/IDBTransaction#mode_constants">mode</a>) باشد، پرتاب می‌شود.
- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این {{domxref("IDBObjectStore")}} غیرفعال باشد، پرتاب می‌شود.
- `DataError` {{domxref("DOMException")}}
  - : اگر هر یک از شرایط زیر اعمال شود، پرتاب می‌شود:
    - object store از کلیدهای درون‌خطی (in-line keys) استفاده می‌کند یا مولد کلید دارد، و یک پارامتر key ارائه شده است.
    - object store از کلیدهای خارج از خط (out-of-line keys) استفاده می‌کند و مولد کلید ندارد، و هیچ پارامتر key ارائه نشده است.
    - object store از کلیدهای درون‌خطی استفاده می‌کند اما مولد کلید ندارد، و مسیر کلید object store یک کلید معتبر تولید نمی‌کند.
    - پارامتر key ارائه شده است اما حاوی یک کلید معتبر نیست.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("IDBObjectStore")}} حذف یا پاک شده باشد، پرتاب می‌شود.
- `DataCloneError` {{domxref("DOMException")}}
  - : اگر داده‌ای که ذخیره می‌شود نتواند توسط الگوریتم clone ساخت‌یافته داخلی clone شود، پرتاب می‌شود.
- `ConstraintError` {{domxref("DOMException")}}
  - : اگر عملیات درج به دلیل نقض محدودیت کلید اصلی (به دلیل وجود یک رکورد از قبل با همان مقدار کلید اصلی) شکست بخورد، پرتاب می‌شود.

## Examples

در قطعه کد زیر، یک تراکنش خواندن/نوشتن روی پایگاه داده خود باز می‌کنیم و با استفاده از `add()` داده‌هایی را به یک object store اضافه می‌کنیم. همچنین به توابع متصل به event handlerهای تراکنش توجه کنید که نتیجه باز شدن تراکنش را در صورت موفقیت یا شکست گزارش می‌دهند. برای یک مثال کامل و قابل اجرا، برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) را ببینید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db variable.
  // This is used a lot below
  db = DBOpenRequest.result;

  // Run the addData() function to add the data to the database
  addData();
};

function addData() {
  // Create a new object ready to insert into the IDB
  const newItem = [
    {
      taskTitle: "Walk dog",
      hours: 19,
      minutes: 30,
      day: 24,
      month: "December",
      year: 2013,
      notified: "no",
    },
  ];

  // open a read/write db transaction, ready for adding the data
  const transaction = db.transaction(["toDoList"], "readwrite");

  // report on the success of the transaction completing, when everything is done
  transaction.oncomplete = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Transaction completed.";
  };

  transaction.onerror = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Transaction not opened due to error. Duplicate items not allowed.";
  };

  // create an object store on the transaction
  const objectStore = transaction.objectStore("toDoList");

  // Make a request to add our newItem object to the object store
  const objectStoreRequest = objectStore.add(newItem[0]);

  objectStoreRequest.onsuccess = (event) => {
    // report the success of our request
    note.appendChild(document.createElement("li")).textContent =
      "Request successful.";
  };
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم یک بازه از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).