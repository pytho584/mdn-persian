---
title: "IDBKeyRange: upperBound() static method"
short-title: upperBound()
slug: Web/API/IDBKeyRange/upperBound_static
page-type: web-api-static-method
browser-compat: api.IDBKeyRange.upperBound_static
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

روش ایستای **`upperBound()`** از رابط {{domxref("IDBKeyRange")}} یک محدوده کلید بالای کران جدید ایجاد می‌کند. به طور پیش‌فرض، این محدوده شامل مقدار نقطه پایانی بالایی است و بسته (closed) است.

## نحو (Syntax)

```js-nolint
IDBKeyRange.upperBound(upper)
IDBKeyRange.upperBound(upper, open)
```

### پارامترها

- `upper`
  - : کران بالایی محدوده کلید جدید را مشخص می‌کند.
- `open` {{optional_inline}}
  - : نشان می‌دهد که آیا کران بالایی مقدار نقطه پایانی را حذف می‌کند یا خیر. مقدار پیش‌فرض `false` است.

### مقدار بازگشتی

{{domxref("IDBKeyRange")}}: محدوده کلید تازه ایجاد شده.

### استثناها

- `DataError` {{domxref("DOMException")}}
  - : اگر کلید مرتبط با پارامتر `upper` یک کلید معتبر نباشد، پرتاب می‌شود.

## مثال‌ها

مثال زیر نحوه استفاده از یک محدوده کلید بالای کران را نشان می‌دهد. در اینجا ما `keyRangeValue = IDBKeyRange.upperBound("F");` را اعلام می‌کنیم — محدوده‌ای که شامل مقدار "F" و همه چیز قبل از آن است. یک تراکنش (با استفاده از {{domxref("IDBTransaction")}}) و یک object store باز می‌کنیم، و یک Cursor با {{domxref("IDBObjectStore.openCursor")}} باز می‌کنیم که `keyRangeValue` را به عنوان مقدار محدوده کلید اختیاری آن اعلام می‌کند.

اگر از `IDBKeyRange.upperBound("F", true);` استفاده کنیم، آنگاه محدوده "F" را حذف می‌کند و در عوض فقط مقادیر قبل از آن را شامل می‌شود.

> [!NOTE]
> برای یک مثال کامل‌تر که به شما امکان آزمایش با محدوده کلید را می‌دهد، به مخزن [IDBKeyRange-example](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbkeyrange) ما نگاهی بیندازید ([همچنین مثال را به صورت زنده مشاهده کنید](https://mdn.github.io/dom-examples/indexeddb-examples/idbkeyrange/).)

```js
function displayData() {
  const keyRangeValue = IDBKeyRange.upperBound("F");

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
- تنظیم یک محدوده از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها (cursors): {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مثال را به صورت زنده مشاهده کنید](https://mdn.github.io/dom-examples/to-do-notifications/)).