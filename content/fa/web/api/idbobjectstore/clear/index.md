---
title: "IDBObjectStore: clear() method"
short-title: clear()
slug: Web/API/IDBObjectStore/clear
page-type: web-api-instance-method
browser-compat: api.IDBObjectStore.clear
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`clear()`** از رابط {{domxref("IDBObjectStore")}} یک شی {{domxref("IDBRequest")}} ایجاد کرده و بلافاصله آن را بازمی‌گرداند، و این object store را در یک رشته جداگانه پاک می‌کند. این کار برای حذف تمام داده‌های فعلی از یک object store است.

پاک کردن یک object store شامل حذف تمام رکوردها از object store و حذف تمام رکوردها در ایندکس‌هایی است که به آن object store ارجاع می‌دهند. برای حذف تنها بخشی از رکوردها در یک store، از {{domxref("IDBObjectStore.delete")}} با ارسال یک کلید یا {{domxref("IDBKeyRange")}} استفاده کنید.

## Syntax

```js-nolint
clear()
```

### Parameters

هیچکدام.

### Return value

یک شی {{domxref("IDBRequest")}} که رویدادهای بعدی مربوط به این عملیات روی آن فعال می‌شوند. اگر عملیات موفقیت‌آمیز باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست `undefined` خواهد بود.

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر object store حذف شده باشد، پرتاب می‌شود.
- `ReadOnlyError` {{domxref("DOMException")}}
  - : اگر تراکنش مرتبط با این عملیات در [حالت فقط-خواندنی](/en-US/docs/Web/API/IDBTransaction/mode) باشد، پرتاب می‌شود.
- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این {{domxref("IDBObjectStore")}} غیرفعال باشد، پرتاب می‌شود.

## Examples

در قطعه کد زیر، یک تراکنش خواندن/نوشتن روی پایگاه داده خود باز می‌کنیم و تمام داده‌های فعلی را با استفاده از `clear()` از object store پاک می‌کنیم. برای یک مثال کامل و قابل اجرا، به برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ما مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db variable.
  // This is used a lot below
  db = DBOpenRequest.result;

  // Clear all the data from the object store
  clearData();
};

function clearData() {
  // open a read/write db transaction, ready for clearing the data
  const transaction = db.transaction(["toDoList"], "readwrite");

  // report on the success of the transaction completing, when everything is done
  transaction.oncomplete = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Transaction completed.";
  };

  transaction.onerror = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      `Transaction not opened due to error: ${transaction.error}`;
  };

  // create an object store on the transaction
  const objectStore = transaction.objectStore("toDoList");

  // Make a request to clear all the data out of the object store
  const objectStoreRequest = objectStore.clear();

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
- تنظیم محدوده کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های شما: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).