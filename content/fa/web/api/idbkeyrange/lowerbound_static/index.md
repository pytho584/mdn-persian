---
title: "IDBKeyRange: lowerBound() static method"
---

---
title: "IDBKeyRange: lowerBound() static method"
short-title: lowerBound()
slug: Web/API/IDBKeyRange/lowerBound_static
page-type: web-api-static-method
browser-compat: api.IDBKeyRange.lowerBound_static
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد ایستای **`lowerBound()`** از رابط {{domxref("IDBKeyRange")}} یک بازه کلید جدید با فقط کران پایین می‌سازد. به‌طور پیش‌فرض، مقدار نقطه پایانی پایین را شامل می‌شود و بازه بسته است.

## سینتکس

```js-nolint
IDBKeyRange.lowerBound(lower)
IDBKeyRange.lowerBound(lower, open)
```

### پارامترها

- `lower`
  - : کران پایین بازه کلید جدید را مشخص می‌کند.
- `open` {{optional_inline}}
  - : نشان می‌دهد که آیا کران پایین مقدار نقطه پایانی را مستثنی می‌کند یا خیر. مقدار پیش‌فرض false است.

### مقدار بازگشتی

{{domxref("IDBKeyRange")}}: بازه کلید تازه ایجاد شده.

### استثناها

- `DataError` {{domxref("DOMException")}}
  - : اگر کلید مرتبط با پارامتر `lower` یک کلید معتبر نباشد، پرتاب می‌شود.

## مثال‌ها

مثال زیر نحوه استفاده از بازه کلید با کران پایین را نشان می‌دهد. در اینجا `keyRangeValue = IDBKeyRange.lowerBound("F", false);` را تعریف می‌کنیم — بازه‌ای که مقدار "F" و همه چیز بعد از آن را شامل می‌شود. یک تراکنش (با استفاده از {{domxref("IDBTransaction")}}) و یک object store باز می‌کنیم و یک Cursor با {{domxref("IDBObjectStore.openCursor")}} باز می‌کنیم و `keyRangeValue` را به عنوان مقدار بازه کلید اختیاری آن تعیین می‌کنیم. این بدان معناست که cursor فقط رکوردهایی با مقدار کلید "F" و تمام مقادیر بعد از آن را بازیابی می‌کند. اگر از `IDBKeyRange.lowerBound("F", true);` استفاده کنیم، آنگاه بازه "F" را شامل نمی‌شود؛ فقط مقادیر بعد از آن.

> [!NOTE]
> برای یک مثال کامل‌تر که به شما امکان آزمایش با بازه کلید را می‌دهد، به مخزن [IDBKeyRange-example](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbkeyrange) ما نگاه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbkeyrange/)).

```js
function displayData() {
  const keyRangeValue = IDBKeyRange.lowerBound("F");

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از cursorها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).