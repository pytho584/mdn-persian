---
title: "IDBCursor: delete() method"
short-title: delete()
slug: Web/API/IDBCursor/delete
page-type: web-api-instance-method
browser-compat: api.IDBCursor.delete
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

متد **`delete()`** از رابط {{domxref("IDBCursor")}} یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک رشته جداگانه، رکورد را در موقعیت مکان‌نما حذف می‌کند، بدون اینکه موقعیت مکان‌نما تغییر کند. پس از حذف رکورد، مقدار مکان‌نما (cursor) روی `null` تنظیم می‌شود.

توجه داشته باشید که نمی‌توانید `delete()` (یا {{domxref("IDBCursor.update()")}}) را روی مکان‌نماهایی که از {{domxref("IDBIndex.openKeyCursor()")}} به دست آمده‌اند فراخوانی کنید. برای چنین نیازهایی، باید به جای آن از {{domxref("IDBIndex.openCursor()")}} استفاده کنید.

## نحو (Syntax)

```js-nolint
delete()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مرتبط با این عملیات روی آن فعال می‌شوند. اگر عملیات موفقیت‌آمیز باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست `undefined` است.

### استثناها (Exceptions)

این متد ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر را ایجاد کند:

- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این IDBCursor غیرفعال باشد.
- `ReadOnlyError` {{domxref("DOMException")}}
  - : اگر حالت تراکنش فقط خواندنی باشد.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر مکان‌نما با استفاده از {{domxref("IDBindex.openKeyCursor")}} ایجاد شده باشد، در حال حاضر در حال تکرار است، یا از انتهای خود عبور کرده باشد.

## مثال‌ها

در این قطعه ساده، یک تراکنش ایجاد می‌کنیم، یک فروشگاه شیء (object store) را بازیابی می‌کنیم، و سپس از یک مکان‌نما برای تکرار روی تمام رکوردهای فروشگاه شیء استفاده می‌کنیم. اگر `albumTitle` مکان‌نمای فعلی برابر با "Grace under pressure" باشد، آن رکورد کامل را با استفاده از `const request = cursor.delete();` حذف می‌کنیم.

مکان‌نما نیازی ندارد که داده‌ها را بر اساس یک کلید انتخاب کنیم؛ می‌توانیم همه آن‌ها را دریافت کنیم. همچنین توجه داشته باشید که در هر تکرار حلقه، می‌توانید داده‌هایی را از رکورد فعلی زیر شیء مکان‌نما با استفاده از `cursor.value.foo` دریافت کنید. برای یک مثال کامل کار، به [مثال IDBCursor](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbcursor) ما مراجعه کنید ([مشاهده مثال به صورت زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbcursor/)).

```js
function deleteResult() {
  list.textContent = "";
  const transaction = db.transaction(["rushAlbumList"], "readwrite");
  const objectStore = transaction.objectStore("rushAlbumList");

  objectStore.openCursor().onsuccess = (event) => {
    const cursor = event.target.result;
    if (cursor) {
      if (cursor.value.albumTitle === "Grace under pressure") {
        const request = cursor.delete();
        request.onsuccess = () => {
          console.log(
            "Deleted that mediocre album from 1984. Even Power windows is better.",
          );
        };
      } else {
        const listItem = document.createElement("li");
        listItem.textContent = `${cursor.value.albumTitle}, ${cursor.value.year}`;
        list.appendChild(listItem);
      }
      cursor.continue();
    } else {
      console.log("Entries displayed.");
    }
  };
}
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از مکان‌نماها: {{domxref("IDBCursor")}}
- مثال مرجع: [اعلان‌های کارهای انجام‌دادنی (To-do Notifications)](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال به صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).