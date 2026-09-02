---
title: "IDBIndex: getKey() method"
short-title: getKey()
slug: Web/API/IDBIndex/getKey
page-type: web-api-instance-method
browser-compat: api.IDBIndex.getKey
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`getKey()`** از رابط {{domxref("IDBIndex")}} یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک رشته‌ی جداگانه، یا کلید اصلیِ متناظر با کلید داده‌شده در این ایندکس را می‌یابد، یا اگر `key` به یک {{domxref("IDBKeyRange")}} تنظیم شده باشد، نخستین کلید اصلیِ متناظر را پیدا می‌کند.

اگر کلید اصلی پیدا شود، به‌عنوان `result` شیء درخواست تنظیم می‌شود. توجه داشته باشید که این متد برخلاف {{domxref("IDBIndex.get")}} کل رکورد را برنمی‌گرداند.

## نحو

```js-nolint
getKey()
getKey(key)
```

### پارامترها

- `key` {{optional_inline}}
  - : یک کلید یا {{domxref("IDBKeyRange")}} که رکورد موردنظر برای بازیابی را مشخص می‌کند. اگر این مقدار `null` باشد یا وجود نداشته باشد، مرورگر از یک محدوده‌ی کلید نامحدود استفاده خواهد کرد.

### مقدار بازگشتی

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مرتبط با این عملیات روی آن رخ می‌دهند.

اگر عملیات با موفقیت انجام شود، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست، کلید نخستین رکوردی است که با کلید یا محدوده‌ی کلید داده‌شده مطابقت دارد.

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر پرتاب کند:

- `TransactionInactiveError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که تراکنش این {{domxref("IDBIndex")}} غیرفعال باشد.
- `DataError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که کلید یا محدوده‌ی کلید ارائه‌شده حاوی یک کلید نامعتبر باشد.
- `InvalidStateError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که {{domxref("IDBIndex")}} حذف یا پاک شده باشد.

## مثال‌ها

در مثال زیر، یک تراکنش و یک مخزن شیء (object store) باز می‌کنیم و سپس ایندکس `lName` را از یک پایگاه‌داده‌ی ساده‌ی مخاطبین می‌گیریم. سپس با استفاده از {{domxref("IDBIndex.openCursor")}} یک نشانگر (cursor) پایه روی ایندکس باز می‌کنیم — این کار دقیقاً مانند باز کردن مستقیم نشانگر روی یک `ObjectStore` با استفاده از {{domxref("IDBObjectStore.openCursor")}} عمل می‌کند، با این تفاوت که رکوردهای بازگشتی بر اساس ایندکس مرتب می‌شوند، نه بر اساس کلید اصلی.

سپس از `myIndex.getKey('Bungle')` برای بازیابی کلید اصلی رکوردی استفاده می‌شود که `lName` آن `Bungle` است، و نتیجه‌ی آن درخواست، هنگام بازگشت فراخوانِ موفقیت (success callback)، در کنسول ثبت می‌شود.

در پایان، روی هر رکورد پیمایش می‌کنیم و داده‌ها را در یک جدول HTML وارد می‌کنیم. برای یک مثال کامل و قابل اجرا، به [مخزن دموی IndexedDB-examples](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbindex) مراجعه کنید ([مشاهده‌ی مثال زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbindex/)).

```js
function displayDataByIndex() {
  tableEntry.textContent = "";
  const transaction = db.transaction(["contactsList"], "readonly");
  const objectStore = transaction.objectStore("contactsList");

  const myIndex = objectStore.index("lName");
  const getKeyRequest = myIndex.getKey("Bungle");
  getKeyRequest.onsuccess = () => {
    console.log(getKeyRequest.result);
  };

  myIndex.openCursor().onsuccess = (event) => {
    const cursor = event.target.result;
    if (cursor) {
      const tableRow = document.createElement("tr");
      for (const cell of [
        cursor.value.id,
        cursor.value.lName,
        cursor.value.fName,
        cursor.value.jTitle,
        cursor.value.company,
        cursor.value.eMail,
        cursor.value.phone,
        cursor.value.age,
      ]) {
        const tableCell = document.createElement("td");
        tableCell.textContent = cell;
        tableRow.appendChild(tableCell);
      }
      tableEntry.appendChild(tableRow);

      cursor.continue();
    } else {
      console.log("Entries all displayed.");
    }
  };
}
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
- بازیابی و اعمال تغییرات در داده‌هایتان: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده‌ی مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).