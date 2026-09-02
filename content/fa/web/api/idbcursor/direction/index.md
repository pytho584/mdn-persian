---
title: "IDBCursor: direction property"
---

---
title: "IDBCursor: direction property"
short-title: direction
slug: Web/API/IDBCursor/direction
page-type: web-api-instance-property
browser-compat: api.IDBCursor.direction
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`direction`** در اینترفیس {{domxref("IDBCursor")}} یک رشته (string) است که جهت پیمایش نشانگر (cursor) را مشخص می‌کند. این جهت برای نمونه با استفاده از {{domxref("IDBObjectStore.openCursor")}} تعیین می‌شود. برای مشاهدهٔ مقادیر ممکن، بخش [مقدار](#مقدار) را ببینید.

## مقدار

رشته‌ای است که جهتی را نشان می‌دهد نشانگر در آن جهت داده‌ها را پیمایش می‌کند. مقادیر ممکن عبارت‌اند از:

- `next`
  - : نشانگر در ابتدای منبع داده باز می‌شود و به سمت انتهای آن حرکت می‌کند.
- `nextunique`
  - : نشانگر در ابتدای منبع داده باز می‌شود و به سمت انتهای آن حرکت می‌کند.
    برای هر کلید دارای مقادیر تکراری، فقط رکوردی که به ابتدای منبع نزدیک‌تر است بازگردانده می‌شود.
- `prev`
  - : نشانگر در انتهای منبع داده باز می‌شود و به سمت ابتدای آن حرکت می‌کند.
- `prevunique`
  - : نشانگر در انتهای منبع داده باز می‌شود و به سمت ابتدای آن حرکت می‌کند.
    برای هر کلید دارای مقادیر تکراری، فقط رکوردی که به ابتدای منبع نزدیک‌تر است بازگردانده می‌شود.

## مثال‌ها

در این قطعه کد ساده، یک تراکنش می‌سازیم، یک object store (مخزن اشیاء) دریافت می‌کنیم و سپس با استفاده از یک نشانگر، همهٔ رکوردهای داخل مخزن اشیاء را پیمایش می‌کنیم. در هر تکرار، جهت نشانگر را در کنسول ثبت (log) می‌کنیم.

> [!NOTE]
> نمی‌توانیم جهت حرکت نشانگر را با استفاده از ویژگی `direction` تغییر دهیم، چون این ویژگی فقط‌خواندنی است. جهت حرکت را با پارامتر دوم {{domxref("IDBObjectStore.openCursor")}} مشخص می‌کنیم.

نشانگر از ما نمی‌خواهد داده‌ها را بر اساس کلید انتخاب کنیم؛ می‌توانیم به‌سادگی همهٔ داده‌ها را بگیریم. همچنین توجه داشته باشید که در هر تکرار حلقه می‌توانید داده‌های رکورد جاری را با `cursor.value.foo` از روی شیء نشانگر بخوانید. برای یک مثال کامل و کاربردی، به [مثال IDBCursor](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbcursor) مراجعه کنید ([مشاهدهٔ مثال به‌صورت زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbcursor/)).

```js
function backwards() {
  list.textContent = "";
  const transaction = db.transaction(["rushAlbumList"], "readonly");
  const objectStore = transaction.objectStore("rushAlbumList");

  objectStore.openCursor(null, "prev").onsuccess = (event) => {
    const cursor = event.target.result;
    if (cursor) {
      const listItem = document.createElement("li");
      listItem.textContent = `${cursor.value.albumTitle}, ${cursor.value.year}`;
      list.appendChild(listItem);

      console.log(cursor.direction);
      cursor.continue();
    } else {
      console.log("Entries displayed backwards.");
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
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).