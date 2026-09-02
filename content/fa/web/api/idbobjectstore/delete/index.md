---
title: "IDBObjectStore: delete() method"
short-title: delete()
slug: Web/API/IDBObjectStore/delete
page-type: web-api-instance-method
browser-compat: api.IDBObjectStore.delete
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

متد **`delete()`** از رابط {{domxref("IDBObjectStore")}} یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک رشته جداگانه، رکورد یا رکوردهای مشخص شده را حذف می‌کند.

می‌توان یک کلید یا یک {{domxref("IDBKeyRange")}} ارسال کرد که امکان حذف یک یا چند رکورد از یک فروشگاه را فراهم می‌کند. برای حذف تمام رکوردهای یک فروشگاه، از {{domxref("IDBObjectStore.clear")}} استفاده کنید.

به خاطر داشته باشید که اگر از یک {{domxref("IDBCursor", "IDBCursor")}} استفاده می‌کنید، می‌توانید از متد {{domxref("IDBCursor.delete()")}} برای حذف کارآمدتر رکورد جاری استفاده کنید — بدون نیاز به جستجوی صریح کلید رکورد.

## نحو

```js-nolint
delete(key)
```

### پارامترها

- `key`
  - : کلید رکوردی که باید حذف شود، یا یک {{domxref("IDBKeyRange")}} برای حذف تمام رکوردهایی که کلیدهایشان در محدوده قرار دارند.

### مقدار بازگشتی

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مربوط به این عملیات روی آن فعال می‌شوند. اگر عملیات موفقیت‌آمیز باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست `undefined` است.

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} از انواع زیر را پرتاب کند:

- `TransactionInactiveError` {{domxref("DOMException")}}
  - : در صورتی که تراکنش این فروشگاه شیء غیرفعال باشد، پرتاب می‌شود.
- `ReadOnlyError` {{domxref("DOMException")}}
  - : در صورتی که حالت تراکنش فروشگاه شیء فقط خواندنی باشد، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : در صورتی که فروشگاه شیء حذف شده باشد، پرتاب می‌شود.
- `DataError` {{domxref("DOMException")}}
  - : در صورتی که `key` یک [کلید معتبر](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#key) یا یک [محدوده کلید](/en-US/docs/Web/API/IDBKeyRange) نباشد، پرتاب می‌شود.

## مثال‌ها

قطعه کد زیر تابع `deleteItem()` را نشان می‌دهد که بخشی از برنامه نمونه اعلان‌های کارهای روزانه است. این برنامه آیتم‌های لیست کارهای روزانه را با استفاده از IndexedDB ذخیره می‌کند. می‌توانید [کد کامل برنامه را در GitHub](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ببینید و [برنامه را به صورت زنده امتحان کنید](https://mdn.github.io/dom-examples/to-do-notifications/).

تابع `deleteItem()` زمانی فراخوانی می‌شود که کاربر روی دکمه حذف یک آیتم لیست کارها کلیک می‌کند. کلید آیتم در ویژگی داده `'data-task'` دکمه تنظیم شده است، بنابراین تابع می‌داند کدام آیتم را حذف کند. تابع یک تراکنش پایگاه داده باز می‌کند که در آن آیتم را با ارائه کلیدش حذف می‌کند. وقتی تراکنش کامل می‌شود، تابع رابط کاربری برنامه را به‌روزرسانی می‌کند تا گزارش دهد که آیتم حذف شده است.

توجه داشته باشید که در این تابع `db` یک متغیر سراسری است که به یک شیء {{domxref("IDBDatabase")}} اشاره می‌کند که هنگام بارگذاری برنامه مقداردهی اولیه می‌شود.

```js
function deleteItem(event) {
  // retrieve the name of the task we want to delete
  let dataTask = event.target.getAttribute("data-task");

  // open a database transaction and delete the task, finding it by the name we retrieved above
  let transaction = db.transaction(["toDoList"], "readwrite");
  let request = transaction.objectStore("toDoList").delete(dataTask);

  // report that the data item has been deleted
  transaction.oncomplete = () => {
    // delete the parent of the button, which is the list item, so it no longer is displayed
    event.target.parentNode.parentNode.removeChild(event.target.parentNode);
    note.appendChild(document.createElement("li")).textContent =
      `Task "${dataTask}" deleted.`;
  };
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم یک محدوده کلید: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [اعلان‌های کارهای روزانه](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/))