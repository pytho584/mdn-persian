---
title: "IDBObjectStore: get() method"
---

---
title: "IDBObjectStore: get() method"
short-title: get()
slug: Web/API/IDBObjectStore/get
page-type: web-api-instance-method
browser-compat: api.IDBObjectStore.get
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`get()`** از رابط {{domxref("IDBObjectStore")}} یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک ترد جداگانه، شیء انتخاب‌شده با کلید مشخص‌شده را بازمی‌گرداند. از این متد برای بازیابی رکوردهای خاص از یک object store (ذخیره‌گاه شیء) استفاده می‌شود.

اگر مقداری با موفقیت یافت شود، یک شبیه‌سازی ساختاریافته از آن ایجاد شده و به‌عنوان [`result`](/en-US/docs/Web/API/IDBRequest/result) شیء درخواست تنظیم می‌شود.

> [!NOTE]
> این متد برای دو حالت نتیجه‌ی یکسانی تولید می‌کند: الف) رکوردی که در پایگاه‌داده وجود ندارد، و ب) رکوردی که مقدار آن تعریف‌نشده (undefined) است.
> برای تشخیص این دو حالت از یکدیگر، متد `openCursor()` را با همان کلید فراخوانی کنید. آن متد اگر رکورد وجود داشته باشد یک cursor برمی‌گرداند و اگر وجود نداشته باشد، هیچ cursory برنمی‌گرداند.

## نحو

```js-nolint
get(key)
```

### پارامترها

- `key`
  - : کلید یا محدوده کلیدی که رکورد مورد نظر برای بازیابی را مشخص می‌کند.

### مقدار بازگشتی

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مرتبط با این عملیات روی آن ارسال می‌شوند. اگر عملیات موفق باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست، مقدار اولین رکوردی است که با کلید یا محدوده کلید داده‌شده مطابقت دارد.

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر ایجاد کند:

- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این {{domxref("IDBObjectStore")}} غیرفعال باشد، صادر می‌شود.
- `DataError` {{domxref("DOMException")}}
  - : اگر کلید یا محدوده کلید ارائه‌شده حاوی کلید نامعتبر باشد، صادر می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("IDBObjectStore")}} حذف شده یا از بین رفته باشد، صادر می‌شود.

## مثال‌ها

در قطعه کد زیر، یک تراکنش خواندن/نوشتن روی پایگاه‌داده باز می‌کنیم و با استفاده از `get()` یک رکورد خاص از object store دریافت می‌کنیم — یک رکورد نمونه با کلید «Walk dog». پس از بازیابی این شیء داده، می‌توانید آن را با جاوااسکریپت معمولی به‌روزرسانی کنید و سپس با استفاده از یک عملیات {{domxref("IDBObjectStore.put", "put()")}} دوباره در پایگاه‌داده قرار دهید. برای یک مثال کامل و قابل اجرا، برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) را ببینید ([view example live](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db variable.
  // This is used a lot below
  db = DBOpenRequest.result;

  // Run the getData() function to get the data from the database
  getData();
};

function getData() {
  // open a read/write db transaction, ready for retrieving the data
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

  // Make a request to get a record by key from the object store
  const objectStoreRequest = objectStore.get("Walk dog");

  objectStoreRequest.onsuccess = (event) => {
    // report the success of our request
    note.appendChild(document.createElement("li")).textContent =
      "Request successful.";

    const myRecord = objectStoreRequest.result;
  };
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از cursor ها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([View the example live](https://mdn.github.io/dom-examples/to-do-notifications/)).