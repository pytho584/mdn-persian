---
title: "IDBCursor: key property"
short-title: key
slug: Web/API/IDBCursor/key
page-type: web-api-instance-property
browser-compat: api.IDBCursor.key
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

ویژگی فقط خواندنی **`key`** از رابط {{domxref("IDBCursor")}}، کلید رکورد در موقعیت فعلی نما (cursor) را برمی‌گرداند. اگر نما خارج از محدوده خود باشد، این ویژگی به `undefined` تنظیم می‌شود. کلید نما می‌تواند هر نوع داده‌ای باشد.

## مقدار

مقداری از هر نوع.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر نما در حال حرکت یا به پایان رسیده باشد، پرتاب می‌شود.

## مثال‌ها

در این قطعه کد ساده، یک تراکنش ایجاد می‌کنیم، یک ذخیره‌گاه شیء (object store) را بازیابی می‌کنیم، سپس از یک نما برای پیمایش تمام رکوردهای موجود در آن ذخیره‌گاه استفاده می‌کنیم. در هر مرحله از پیمایش، کلید نما را در کنسول ثبت می‌کنیم.

نما نیازی ندارد که داده‌ها را بر اساس یک کلید انتخاب کنیم؛ می‌توانیم همه آنها را دریافت کنیم. همچنین توجه داشته باشید که در هر تکرار حلقه، می‌توانید داده‌های مربوط به رکورد جاری را از طریق `cursor.value.foo` دریافت کنید. برای یک مثال کامل و قابل اجرا، به [IDBCursor example](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbcursor) مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbcursor/)).

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

      console.log(cursor.key);
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
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نماها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).