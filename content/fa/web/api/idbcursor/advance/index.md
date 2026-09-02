---
title: "IDBCursor: advance() method"
short-title: advance()
slug: Web/API/IDBCursor/advance
page-type: web-api-instance-method
browser-compat: api.IDBCursor.advance
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

متد **`advance()`** از رابط {{domxref("IDBCursor")}} مشخص می‌کند که مکان‌نما چند بار باید به جلو حرکت کند.

## Syntax

```js-nolint
advance(count)
```

### Parameters

- `count`
  - : تعداد دفعاتی که مکان‌نما باید به جلو حرکت کند.

### Return value

هیچ ({{jsxref("undefined")}}).

### Exceptions

این متد ممکن است یک {{domxref("DOMException")}} از انواع زیر صادر کند:

- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این `IDBCursor` غیرفعال باشد، صادر می‌شود.
- {{jsxref("TypeError")}}
  - : اگر مقدار ارسال‌شده به پارامتر `count` صفر یا عددی منفی باشد، صادر می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر مکان‌نما در حال حاضر در حال پیمایش باشد یا از انتهای خود عبور کرده باشد، صادر می‌شود.

## Examples

در این قطعهٔ ساده، یک تراکنش ایجاد می‌کنیم، یک object store (مخزن اشیاء) دریافت می‌کنیم و سپس با استفاده از یک مکان‌نما، رکوردهای موجود در آن را پیمایش می‌کنیم. در اینجا از `cursor.advance(2)` استفاده می‌کنیم تا هر بار ۲ مرحله به جلو بپرد؛ یعنی فقط یکی در میان نتایج نمایش داده می‌شود. `advance()` به شکلی مشابه {{domxref("IDBCursor.continue")}} کار می‌کند، با این تفاوت که به شما اجازه می‌دهد چند رکورد را به‌یک‌باره رد کنید، نه اینکه فقط همیشه به رکورد بعدی بروید.

توجه داشته باشید که در هر تکرار حلقه می‌توانید داده‌های رکورد جاری را با استفاده از `cursor.value.foo` از شیء مکان‌نما دریافت کنید. برای یک مثال کامل و قابل اجرا، به [مثال IDBCursor](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbcursor) مراجعه کنید ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbcursor/)).

```js
function advanceResult() {
  list.textContent = "";
  const transaction = db.transaction(["rushAlbumList"], "readonly");
  const objectStore = transaction.objectStore("rushAlbumList");

  objectStore.openCursor().onsuccess = (event) => {
    const cursor = event.target.result;
    if (cursor) {
      const listItem = document.createElement("li");
      listItem.textContent = `${cursor.value.albumTitle}, ${cursor.value.year}`;
      list.appendChild(listItem);
      cursor.advance(2);
    } else {
      console.log("Every other entry displayed.");
    }
  };
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدودهٔ کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و تغییر داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از مکان‌نماها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).