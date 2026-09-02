---
title: "IDBIndex: get() method"
short-title: get()
slug: Web/API/IDBIndex/get
page-type: web-api-instance-method
browser-compat: api.IDBIndex.get
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`get()`** از رابط {{domxref("IDBIndex")}} یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک نخ جداگانه، یا مقدار متناظر با کلید داده‌شده را در فروشگاه شیء ارجاع‌شده پیدا می‌کند، یا نخستین مقدار متناظر را — در صورتی که `key` به‌صورت یک {{domxref("IDBKeyRange")}} تنظیم شده باشد.

اگر مقداری پیدا شود، یک رونوشت ساختاریافته (structured clone) از آن ساخته شده و به‌عنوان `result` شیء درخواست تنظیم می‌شود؛ به این ترتیب، رکورد مرتبط با کلید بازگردانده می‌شود.

### سینتکس

```js-nolint
get()
get(key)
```

### پارامترها

- `key` {{optional_inline}}
  - : کلیدی یا {{domxref("IDBKeyRange")}} که رکورد موردنظر برای بازیابی را مشخص می‌کند. اگر این مقدار `null` باشد یا ارائه نشود، مرورگر از یک بازه کلید نامحدود استفاده خواهد کرد.

### مقدار بازگشتی

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مرتبط با این عملیات روی آن صادر می‌شوند.

اگر عملیات موفقیت‌آمیز باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست، مقدار نخستین رکورد منطبق با کلید یا بازه کلید داده‌شده خواهد بود.

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر را پرتاب کند:

- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این {{domxref("IDBIndex")}} غیرفعال باشد، پرتاب می‌شود.
- `DataError` {{domxref("DOMException")}}
  - : اگر کلید یا بازه کلید ارائه‌شده شامل یک کلید نامعتبر باشد، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("IDBIndex")}} حذف یا برداشته شده باشد، پرتاب می‌شود.

### مثال‌ها

در مثال زیر، یک تراکنش و یک فروشگاه شیء باز می‌کنیم و سپس ایندکس `lName` را از یک پایگاه‌داده ساده مخاطبین می‌گیریم. سپس با استفاده از {{domxref("IDBIndex.openCursor")}} یک کرسر پایه روی ایندکس باز می‌کنیم — این کار دقیقاً مانند باز کردن مستقیم کرسر روی یک `ObjectStore` با {{domxref("IDBObjectStore.openCursor")}} است، با این تفاوت که رکوردهای بازگردانده‌شده بر اساس ایندکس مرتب می‌شوند، نه بر اساس کلید اصلی.

سپس از `myIndex.get('Bungle')` برای بازیابی رکوردی با `lName` برابر با `Bungle` استفاده می‌شود و هنگام اجرای callback موفقیت آن، نتیجه این درخواست در کنسول ثبت می‌شود.

در نهایت، تمام رکوردها را پیمایش می‌کنیم و داده‌ها را در یک جدول HTML درج می‌کنیم. برای مشاهده یک مثال کامل و قابل اجرا، به [مخزن دموی IndexedDB-examples](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbindex) مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbindex/)).

```js
function displayDataByIndex() {
  tableEntry.textContent = "";
  const transaction = db.transaction(["contactsList"], "readonly");
  const objectStore = transaction.objectStore("contactsList");

  const myIndex = objectStore.index("lName");
  const getRequest = myIndex.get("Bungle");
  getRequest.onsuccess = () => {
    console.log(getRequest.result);
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

### مشخصات

{{Specifications}}

### سازگاری مرورگر

{{Compat}}

### همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- کار با تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی داده‌ها و اعمال تغییرات روی آن‌ها: {{domxref("IDBObjectStore")}}
- کار با کرسرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).