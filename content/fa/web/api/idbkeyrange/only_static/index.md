---
title: "IDBKeyRange: only() static method"
short-title: only()
slug: Web/API/IDBKeyRange/only_static
page-type: web-api-static-method
browser-compat: api.IDBKeyRange.only_static
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد ایستای **`only()`** از رابط {{domxref("IDBKeyRange")}} یک محدوده کلید جدید (key range) ایجاد می‌کند که فقط یک مقدار را شامل می‌شود.

## نحو (Syntax)

```js-nolint
IDBKeyRange.only(value)
```

### پارامترها

- `value`
  - : مقدار محدوده کلید جدید.

### مقدار بازگشتی

{{domxref("IDBKeyRange")}}: محدوده کلید جدید ایجاد شده.

### استثناها (Exceptions)

- `DataError` {{domxref("DOMException")}}
  - : اگر پارامتر `value` یک کلید معتبر نباشد، این استثنا پرتاب می‌شود.

## مثال‌ها

مثال زیر نحوه استفاده از یک محدوده کلید تک‌مقداری (only key range) را نشان می‌دهد. در اینجا یک `keyRangeValue = IDBKeyRange.only("A");` اعلام می‌کنیم — محدوده‌ای که فقط مقدار "A" را شامل می‌شود. یک تراکنش (transaction) با استفاده از {{domxref("IDBTransaction")}} و یک فروشگاه شیء (object store) باز می‌کنیم و یک کرسر (cursor) با {{domxref("IDBObjectStore.openCursor")}} باز می‌کنیم و `keyRangeValue` را به عنوان مقدار محدوده کلید اختیاری آن اعلام می‌کنیم. این بدان معناست که کرسر فقط رکوردی با مقدار کلید "A" را بازیابی می‌کند.

> [!NOTE]
> برای یک مثال کامل‌تر که به شما امکان آزمایش با محدوده کلید را می‌دهد، به مخزن [IDBKeyRange](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbkeyrange) ما مراجعه کنید (همچنین [مثال را به صورت زنده مشاهده کنید](https://mdn.github.io/dom-examples/indexeddb-examples/idbkeyrange/)).

```js
function displayData() {
  const keyRangeValue = IDBKeyRange.only("A");

  const transaction = db.transaction(["fThings"], "readonly");
  const objectStore = transaction.objectStore("fThings");

  objectStore.openCursor(keyRangeValue).onsuccess = (event) => {
    const cursor = event.target.result;
    if (cursor) {
      const listItem = document.createElement("li");
      listItem.textContent = `${cursor.value.fThing}, ${cursor.value.fRating}`;
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

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از کرسرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مثال را به صورت زنده مشاهده کنید](https://mdn.github.io/dom-examples/to-do-notifications/)).