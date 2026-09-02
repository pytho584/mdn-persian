---
title: "IDBCursor: continue() method"
short-title: continue()
slug: Web/API/IDBCursor/continue
page-type: web-api-instance-method
browser-compat: api.IDBCursor.continue
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

متد **`continue()`** از رابط {{domxref("IDBCursor")}} مکان‌نما را در امتداد جهت حرکت خود به موقعیت بعدی می‌برد؛ یعنی به آیتمی که کلیدش با پارامتر اختیاری `key` مطابقت دارد. اگر کلیدی مشخص نشود، مکان‌نما بر اساس جهت خود به موقعیت بلافاصله بعدی می‌رود.

## نحو

```js-nolint
continue()
continue(key)
```

### پارامترها

- `key` {{optional_inline}}
  - : کلیدی که مکان‌نما باید در آن قرار گیرد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} از انواع زیر ایجاد کند:

- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این `IDBCursor` غیرفعال باشد پرتاب می‌شود.
- `DataError` {{domxref("DOMException")}}
  - : اگر پارامتر `key` هر یک از شرایط زیر را داشته باشد پرتاب می‌شود:
    - کلید معتبر نباشد.
    - کلید کمتر یا مساوی موقعیت فعلی مکان‌نما باشد و جهت مکان‌نما `next` یا `nextunique` باشد.
    - کلید بزرگ‌تر یا مساوی موقعیت فعلی مکان‌نما باشد و جهت مکان‌نما `prev` یا `prevunique` باشد.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر مکان‌نما در حال پیمایش باشد یا از انتهای خود گذشته باشد پرتاب می‌شود.

## مثال‌ها

در این قطعه ساده، یک تراکنش می‌سازیم، یک object store (فضای ذخیره‌سازی اشیاء) بازیابی می‌کنیم و سپس با استفاده از یک مکان‌نما تمام رکوردهای موجود در object store را پیمایش می‌کنیم. مکان‌نما نیازی ندارد که داده‌ها را بر اساس کلید انتخاب کنیم؛ می‌توانیم همه آن‌ها را برداریم. همچنین توجه داشته باشید که در هر تکرار حلقه، می‌توانید داده‌های رکورد فعلی زیر شیء مکان‌نما را با استفاده از `cursor.value.foo` دریافت کنید. برای یک مثال کامل و قابل اجرا، به [نمونه IDBCursor](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbcursor) مراجعه کنید ([مشاهده مثال به‌صورت زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbcursor/)).

```js
function displayData() {
  const transaction = db.transaction(["rushAlbumList"], "readonly");
  const objectStore = transaction.objectStore("rushAlbumList");

  objectStore.openCursor().onsuccess = (event) => {
    const cursor = event.target.result;
    if (cursor) {
      const listItem = document.createElement("li");
      listItem.textContent = `${cursor.value.albumTitle}, ${cursor.value.year}`;
      list.appendChild(listItem);

      cursor.continue();
    } else {
      console.log("Entries all displayed.");
    }
  };
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از مکان‌نماها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).