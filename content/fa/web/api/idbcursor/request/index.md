---
title: "IDBCursor: request property"
---

---
title: "IDBCursor: request property"
short-title: request
slug: Web/API/IDBCursor/request
page-type: web-api-instance-property
browser-compat: api.IDBCursor.request
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`request`** از رابط {{domxref("IDBCursor")}}، شیء {{domxref("IDBRequest")}} مورد استفاده برای دریافت نشانگر را برمی‌گرداند.

## مقدار

یک نمونه از شیء {{domxref("IDBRequest")}}.

## مثال‌ها

وقتی یک نشانگر را باز می‌کنید، ویژگی `request` روی آن شیء نشانگر در دسترس است تا مشخص کند نشانگر از کدام شیء درخواست سرچشمه گرفته است. برای مثال:

```js
function displayData() {
  list.textContent = "";
  const transaction = db.transaction(["rushAlbumList"], "readonly");
  const objectStore = transaction.objectStore("rushAlbumList");

  const request = objectStore.openCursor();

  request.onsuccess = (event) => {
    const cursor = event.target.result;
    if (cursor) {
      const listItem = document.createElement("li");
      listItem.textContent = `${cursor.value.albumTitle}, ${cursor.value.year}`;
      list.appendChild(listItem);
      console.log(cursor.request);
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
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- نمونه مرجع: [اعلان‌های کارها](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).