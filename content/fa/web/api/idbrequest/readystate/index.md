---
title: "IDBRequest: readyState property"
short-title: readyState
slug: Web/API/IDBRequest/readyState
page-type: web-api-instance-property
browser-compat: api.IDBRequest.readyState
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

خاصیت فقط خواندنی **`readyState`** از رابط {{domxref("IDBRequest")}} وضعیت درخواست را برمی‌گرداند.

هر درخواست در حالت `pending` شروع می‌شود. هنگامی که درخواست با موفقیت کامل شود یا خطایی رخ دهد، وضعیت به `done` تغییر می‌کند.

## مقدار

یکی از رشته‌های زیر:

- `pending`
  - : اگر درخواست هنوز در حال انجام باشد برگردانده می‌شود.
- `done`
  - : اگر درخواست قبلاً تکمیل شده باشد برگردانده می‌شود.

## مثال‌ها

مثال زیر یک رکورد با عنوان مشخص را درخواست می‌کند، `onsuccess` رکورد مرتبط را از {{domxref("IDBObjectStore")}} (که به صورت `objectStoreTitleRequest.result` در دسترس است) دریافت می‌کند، یک ویژگی از رکورد را به‌روزرسانی می‌کند و سپس رکورد به‌روزرسانی شده را در یک درخواست دیگر به object store بازمی‌گرداند. `readyState` درخواست دوم در کنسول توسعه‌دهنده ثبت می‌شود. برای یک مثال کامل کاربردی، برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ما را ببینید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
const title = "Walk dog";

// Open up a transaction as usual
const objectStore = db
  .transaction(["toDoList"], "readwrite")
  .objectStore("toDoList");

// Get the to-do list object that has this title as its title
const objectStoreTitleRequest = objectStore.get(title);

objectStoreTitleRequest.onsuccess = () => {
  // Grab the data object returned as the result
  const data = objectStoreTitleRequest.result;

  // Update the notified value in the object to "yes"
  data.notified = "yes";

  // Create another request that inserts the item
  // back into the database
  const updateTitleRequest = objectStore.put(data);

  // Log the readyState of this request
  console.log(
    `The readyState of this request is ${updateTitleRequest.readyState}`,
  );

  // When this new request succeeds, run the displayData()
  // function again to update the display
  updateTitleRequest.onsuccess = () => {
    displayData();
  };
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
- تنظیم یک محدوده از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از کرسرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).