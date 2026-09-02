---
title: "IDBRequest: result property"
short-title: result
slug: Web/API/IDBRequest/result
page-type: web-api-instance-property
browser-compat: api.IDBRequest.result
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`result`** در رابط {{domxref("IDBRequest")}} نتیجهٔ درخواست را بازمی‌گرداند.

مقدار آن به درخواستی که انجام شده بستگی دارد. برای مثال، متدهای {{domxref("IDBObjectStore.getAllRecords()")}} و {{domxref("IDBIndex.getAllRecords()")}} پس از تکمیل موفقیت‌آمیز درخواست، این ویژگی را با آرایه‌ای از نمونه‌های {{domxref("IDBRecord")}} پر می‌کنند.

## مقدار

any.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که بخواهید به این ویژگی دسترسی پیدا کنید، در حالی که درخواست تکمیل نشده است و بنابراین نتیجه در دسترس نیست.

## مثال‌ها

### استفادهٔ پایه

مثال زیر عنوان یک رکورد مشخص را درخواست می‌کند. در صورت موفقیت، رکورد مرتبط از {{domxref("IDBObjectStore")}} بازیابی می‌شود (از طریق `objectStoreTitleRequest.result` در دسترس قرار می‌گیرد)، یکی از ویژگی‌های رکورد به‌روزرسانی می‌شود و سپس رکورد به‌روزرسانی‌شده دوباره در object store قرار می‌گیرد. برای مشاهدهٔ یک مثال کامل و قابل اجرا، برنامهٔ [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) را ببینید ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
const title = "Walk dog";

// Open up a transaction as usual
const objectStore = db
  .transaction(["toDoList"], "readwrite")
  .objectStore("toDoList");

// Get the to-do list object that has this title as its title
const objectStoreTitleRequest = objectStore.get(title);

objectStoreTitleRequest.addEventListener("success", () => {
  // Grab the data object returned as the result
  const data = objectStoreTitleRequest.result;

  // Update the notified value in the object to "yes"
  data.notified = "yes";

  // Create another request that inserts the item
  // back into the database
  const updateTitleRequest = objectStore.put(data);

  // When this new request succeeds, run the displayData()
  // function again to update the display
  updateTitleRequest.addEventListener("success", () => {
    displayData();
  });
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییر در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها (cursors): {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).