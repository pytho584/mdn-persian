---
title: "IDBIndex: count() method"
short-title: count()
slug: Web/API/IDBIndex/count
page-type: web-api-instance-method
browser-compat: api.IDBIndex.count
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`count()`** از رابط {{domxref("IDBIndex")}} یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک رشتهٔ جداگانه، تعداد رکوردهای موجود در یک بازهٔ کلید را برمی‌گرداند.

## سینتکس

```js-nolint
count()
count(key)
```

### پارامترها

- `key` {{optional_inline}}
  - : کلید یا بازهٔ کلیدی که رکورد موردنظر برای شمارش را مشخص می‌کند.

### مقدار بازگشتی

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مرتبط با این عملیات روی آن ارسال می‌شوند.

اگر عملیات موفق باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست، تعداد رکوردهایی است که با کلید یا بازهٔ کلید داده‌شده مطابقت دارند.

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر را پرتاب کند:

- `TransactionInactiveError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که تراکنش این {{domxref("IDBIndex")}} غیرفعال باشد.
- `DataError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که کلید یا بازهٔ کلید ارائه‌شده حاوی یک کلید نامعتبر باشد.
- `InvalidStateError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که {{domxref("IDBIndex")}} حذف یا برداشته شده باشد.

## مثال‌ها

در مثال زیر، یک تراکنش و یک object store باز می‌کنیم، سپس ایندکس `lName` را از یک پایگاه‌دادهٔ سادهٔ مخاطبین دریافت می‌کنیم. سپس با استفاده از {{domxref("IDBIndex.openCursor")}} یک cursor پایه روی ایندکس باز می‌کنیم — این کار مشابه باز کردن یک cursor مستقیماً روی یک `ObjectStore` با استفاده از {{domxref("IDBObjectStore.openCursor")}} است، با این تفاوت که رکوردهای بازگشتی بر اساس ایندکس مرتب می‌شوند، نه بر اساس کلید اصلی.

سپس از `myIndex.count()` برای شمارش تعداد رکوردهای ایندکس استفاده می‌شود و نتیجهٔ این درخواست وقتی callback موفقیت آن برمی‌گردد، در کنسول ثبت می‌شود.

در نهایت، روی هر رکورد پیمایش می‌کنیم و داده‌ها را در یک جدول HTML درج می‌کنیم. برای یک مثال کامل و قابل اجرا، به [مخزن دموی IndexedDB-examples](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbindex) مراجعه کنید ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbindex/)).

```js
function displayDataByIndex() {
  tableEntry.textContent = "";
  const transaction = db.transaction(["contactsList"], "readonly");
  const objectStore = transaction.objectStore("contactsList");

  const myIndex = objectStore.index("lName");
  const countRequest = myIndex.count();
  countRequest.onsuccess = () => {
    console.log(countRequest.result);
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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از cursorها: {{domxref("IDBCursor")}}
- مثال مرجع: [اعلان‌های کارهای روزانه](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).