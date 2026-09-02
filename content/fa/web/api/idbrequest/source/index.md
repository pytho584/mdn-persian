---
title: "IDBRequest: source property"
short-title: source
slug: Web/API/IDBRequest/source
page-type: web-api-instance-property
browser-compat: api.IDBRequest.source
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`source`** در رابط {{domxref("IDBRequest")}} منبع درخواست را برمی‌گرداند، مانند یک Index یا object store. اگر منبعی وجود نداشته باشد (مثلاً هنگام فراخوانی {{domxref("IDBFactory.open")}})، مقدار `null` برمی‌گردد.

## مقدار

یک شیء که منبع درخواست را نشان می‌دهد، مانند یک {{domxref("IDBIndex")}}، {{domxref("IDBObjectStore")}} یا {{domxref("IDBCursor")}}.

## مثال‌ها

مثال زیر یک عنوان رکورد مشخص را درخواست می‌کند؛ در `onsuccess` رکورد مرتبط از {{domxref("IDBObjectStore")}} گرفته می‌شود (با نام `objectStoreTitleRequest.result` در دسترس است)، یک ویژگی از رکورد به‌روزرسانی می‌شود و سپس رکورد به‌روزرسانی‌شده در یک درخواست دیگر دوباره در object store قرار می‌گیرد. منبع دومین درخواست در کنسول توسعه‌دهنده ثبت (log) می‌شود. برای یک مثال کامل و قابل اجرا، برنامهٔ [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) را ببینید ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

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

  // Log the source of this request
  console.log(`The source of this request is ${updateTitleRequest.source}`);
  // When this new request succeeds, run the displayData()
  // function again to update the display
  updateTitleRequest.onsuccess = () => {
    displayData();
  };
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و اعمال تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها (cursors): {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).