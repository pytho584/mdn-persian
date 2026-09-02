---
title: "IDBObjectStore: put() method"
short-title: put()
slug: Web/API/IDBObjectStore/put
page-type: web-api-instance-method
browser-compat: api.IDBObjectStore.put
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`put()`** از رابط {{domxref("IDBObjectStore")}} یک رکورد مشخص را در پایگاه داده به‌روزرسانی می‌کند، یا اگر مورد داده شده وجود نداشته باشد، یک رکورد جدید درج می‌کند.

این متد یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک ریسه جداگانه، یک [clone ساختاریافته](https://html.spec.whatwg.org/multipage/common-dom-interfaces.html#structured-clone) از مقدار ایجاد کرده و آن را در object store ذخیره می‌کند. این کار برای افزودن رکوردهای جدید یا به‌روزرسانی رکوردهای موجود در یک object store زمانی که حالت تراکنش `readwrite` است، انجام می‌شود. اگر رکورد با موفقیت ذخیره شود، یک رویداد `success` بر روی شیء درخواست بازگشتی شلیک می‌شود که در آن `result` برابر با کلید رکورد ذخیره شده و `transaction` برابر با تراکنشی است که این object store در آن باز شده است.

متد `put` یک متد _به‌روزرسانی یا درج_ است.
برای یک متد _فقط درج_ به {{domxref("IDBObjectStore.add")}} مراجعه کنید.

به خاطر داشته باشید اگر یک {{domxref("IDBCursor","IDBCursor")}} به رکوردی که می‌خواهید به‌روزرسانی کنید دارید، به‌روزرسانی آن با {{domxref("IDBCursor.update()")}} ارجحیت دارد نسبت به استفاده از `IDBObjectStore.put()`. این کار明確 می‌کند که یک رکورد موجود به‌روزرسانی می‌شود، نه اینکه یک رکورد جدید درج شود.

## Syntax

```js-nolint
put(item)
put(item, key)
```

### Parameters

- `item`
  - : موردی که می‌خواهید به‌روزرسانی (یا درج) کنید.
- `key` {{optional_inline}}
  - : کلید اصلی رکوردی که می‌خواهید به‌روزرسانی کنید (مثلاً از {{domxref("IDBCursor.primaryKey")}}).

### Return value

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مربوط به این عملیات روی آن شلیک می‌شوند.

اگر عملیات موفقیت‌آمیز باشد، مقدار خاصیت {{domxref("IDBRequest.result", "result")}} درخواست، کلید رکورد جدید یا به‌روزرسانی‌شده است.

### Exceptions

این متد ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر را ایجاد کند:

- `ReadOnlyError` {{domxref("DOMException")}}
  - : اگر تراکنش مرتبط با این عملیات در حالت فقط-خواندنی (<a href="/en-US/docs/Web/API/IDBTransaction#mode_constants">mode</a>) باشد، ایجاد می‌شود.
- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این {{domxref("IDBObjectStore")}} غیرفعال باشد، ایجاد می‌شود.
- `DataError` {{domxref("DOMException")}}
  - : اگر هر یک از شرایط زیر برقرار باشد، ایجاد می‌شود:
    - object store از [کلیدهای درون خطی](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#in-line_key) یا [تولیدکننده کلید](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#key_generator) استفاده می‌کند و یک پارامتر `key` ارائه شده است.
    - object store از کلیدهای برون خطی استفاده می‌کند و تولیدکننده کلید ندارد و هیچ پارامتر `key` ارائه نشده است.
    - object store از کلیدهای درون خطی استفاده می‌کند اما تولیدکننده کلید ندارد و [مسیر کلید](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#key_path) object store یک کلید معتبر تولید نمی‌کند.
    - پارامتر `key` ارائه شده است اما حاوی یک کلید معتبر نیست.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("IDBObjectStore")}} حذف یا پاک شده باشد، ایجاد می‌شود.
- `DataCloneError` {{domxref("DOMException")}}
  - : اگر داده‌های ذخیره‌شده نتوانند توسط الگوریتم clone ساختاریافته داخلی clone شوند، ایجاد می‌شود.

## Examples

مثال زیر یک عنوان مشخص را درخواست می‌کند؛ وقتی آن درخواست موفقیت‌آمیز باشد، تابع `onsuccess` رکورد مرتبط را از {{domxref("IDBObjectStore")}} (که به عنوان `objectStoreTitleRequest.result` در دسترس است) می‌گیرد، یک ویژگی از رکورد را به‌روزرسانی می‌کند و سپس رکورد به‌روزرسانی‌شده را با استفاده از `put()` در یک درخواست دیگر به object store بازمی‌گرداند. برای یک مثال کامل کارآمد، به برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ما مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

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

  // Create another request that inserts the item back into the database
  const updateTitleRequest = objectStore.put(data);

  // Log the transaction that originated this request
  console.log(
    `The transaction that originated this request is ${updateTitleRequest.transaction}`,
  );

  // When this new request succeeds, run the displayData() function again to update the display
  updateTitleRequest.onsuccess = () => {
    displayData();
  };
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).