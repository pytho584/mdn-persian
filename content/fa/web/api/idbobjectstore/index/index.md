---
title: "IDBObjectStore: index() method"
---

---
title: "IDBObjectStore: index() method"
short-title: index()
slug: Web/API/IDBObjectStore/index
page-type: web-api-instance-method
browser-compat: api.IDBObjectStore.index
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`index()`** در رابط {{domxref("IDBObjectStore")}} یک ایندکس نام‌گذاری‌شده را در object store جاری باز می‌کند؛ پس از آن می‌توان از آن برای مثال برای بازگرداندن یک سری رکورد مرتب‌شده بر اساس آن ایندکس با استفاده از یک cursor استفاده کرد.

## سینتکس

```js-nolint
index(name)
```

### پارامترها

- `name`
  - : نام ایندکسی که قرار است باز شود.

### مقدار بازگشتی

یک شیء {{domxref("IDBIndex")}} برای دسترسی به ایندکس.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر object store مبدأ حذف شده باشد، یا تراکنش مربوط به object store به پایان رسیده باشد، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر ایندکسی با نام داده‌شده (به‌صورت حساس به بزرگی/کوچکی حروف) در پایگاه‌داده وجود نداشته باشد، پرتاب می‌شود.

## مثال‌ها

در مثال زیر، یک تراکنش و یک object store باز می‌کنیم و سپس ایندکس `lName` را از یک پایگاه‌داده ساده مخاطبین می‌گیریم. سپس یک cursor پایه روی ایندکس با استفاده از {{domxref("IDBIndex.openCursor")}} باز می‌کنیم — این کار همانند باز کردن مستقیم cursor روی یک `ObjectStore` با {{domxref("IDBObjectStore.openCursor")}} عمل می‌کند، با این تفاوت که رکوردهای بازگشت‌داده‌شده بر اساس ایندکس مرتب می‌شوند، نه بر اساس کلید اصلی.

در پایان، از میان هر رکورد عبور می‌کنیم و داده‌ها را در یک جدول HTML وارد می‌کنیم. برای یک مثال کامل و قابل اجرا، به [مثال IDBIndex در مخزن دموی IndexedDB-examples](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbindex) مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbindex/)).

```js
function displayDataByIndex() {
  tableEntry.textContent = "";
  const transaction = db.transaction(["contactsList"], "readonly");
  const objectStore = transaction.objectStore("contactsList");

  const myIndex = objectStore.index("lName");
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
- مثال مرجع: [اعلان‌های کارهای روزانه](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).