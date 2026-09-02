---
title: "IDBKeyRange: bound() static method"
short-title: bound()
slug: Web/API/IDBKeyRange/bound_static
page-type: web-api-static-method
browser-compat: api.IDBKeyRange.bound_static
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد ایستای **`bound()`** در رابط {{domxref("IDBKeyRange")}} یک محدوده کلید جدید با کران‌های بالا و پایین مشخص شده ایجاد می‌کند. کران‌ها می‌توانند باز (یعنی کران‌ها مقادیر نقطه پایانی را حذف کنند) یا بسته (یعنی کران‌ها مقادیر نقطه پایانی را شامل شوند) باشند. به طور پیش‌فرض، کران‌ها بسته هستند.

## نحو (Syntax)

```js-nolint
IDBKeyRange.bound(lower, upper)
IDBKeyRange.bound(lower, upper, lowerOpen)
IDBKeyRange.bound(lower, upper, lowerOpen, upperOpen)
```

### پارامترها

- `lower`
  - : کران پایینی محدوده کلید جدید را مشخص می‌کند.
- `upper`
  - : کران بالایی محدوده کلید جدید را مشخص می‌کند.
- `lowerOpen` {{optional_inline}}
  - : نشان می‌دهد آیا کران پایینی مقدار نقطه پایانی را حذف می‌کند. پیش‌فرض false است.
- `upperOpen` {{optional_inline}}
  - : نشان می‌دهد آیا کران بالایی مقدار نقطه پایانی را حذف می‌کند. پیش‌فرض false است.

### مقدار بازگشتی

{{domxref("IDBKeyRange")}}: محدوده کلید جدید ایجاد شده.

### استثناها (Exceptions)

- `DataError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که یکی از شرایط زیر برقرار باشد:
    - پارامترهای پایینی یا بالایی یک کلید معتبر دریافت نکرده باشند.
    - کلید پایینی بزرگتر از کلید بالایی باشد.
    - کلید پایینی و کلید بالایی برابر باشند و یکی از کران‌ها باز باشد.

## مثال‌ها

مثال زیر نحوه استفاده از یک محدوده کلید کران‌دار را نشان می‌دهد. در اینجا ما یک `keyRangeValue = IDBKeyRange.bound("A", "F");` اعلام می‌کنیم — یک محدوده بین مقادیر "A" و "F". یک تراکنش (با استفاده از {{domxref("IDBTransaction")}}) و یک Object Store باز می‌کنیم، و یک Cursor با {{domxref("IDBObjectStore.openCursor")}} باز می‌کنیم و `keyRangeValue` را به عنوان مقدار محدوده کلید اختیاری آن اعلام می‌کنیم. این بدان معناست که Cursor فقط رکوردهایی با کلیدهای داخل آن محدوده را دریافت می‌کند. این محدوده شامل مقادیر "A" و "F" نیز می‌شود، زیرا ما اعلام نکرده‌ایم که کران‌ها باز باشند. اگر از `IDBKeyRange.bound("A", "F", true, true);` استفاده می‌کردیم، آنگاه محدوده شامل `"A"` و `"F"` نمی‌شد، فقط مقادیر بین آنها را شامل می‌شد.

> [!NOTE]
> برای یک مثال کامل‌تر که به شما امکان آزمایش با محدوده کلید را می‌دهد، به دایرکتوری idbkeyrange در مخزن [indexeddb-examples](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbkeyrange) مراجعه کنید. (همچنین مثال را به صورت [زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbkeyrange/) مشاهده کنید.)

```js
function displayData() {
  const keyRangeValue = IDBKeyRange.bound("A", "F");

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

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم یک محدوده از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از Cursorها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).