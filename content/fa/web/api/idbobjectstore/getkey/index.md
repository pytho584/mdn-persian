---
title: "IDBObjectStore: getKey() method"
short-title: getKey()
slug: Web/API/IDBObjectStore/getKey
page-type: web-api-instance-method
browser-compat: api.IDBObjectStore.getKey
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`getKey()`** از رابط {{domxref("IDBObjectStore")}} یک شیء {{domxref("IDBRequest")}} را برمی‌گرداند و در یک نخ جداگانه، کلید انتخاب‌شده توسط کوئری مشخص‌شده را بازمی‌گرداند. این متد برای بازیابی رکوردهای خاص از یک object store استفاده می‌شود.

اگر یک کلید با موفقیت پیدا شود، یک کپی ساختاریافته از آن ایجاد شده و به عنوان نتیجهٔ شیء درخواست تنظیم می‌شود.

## Syntax

```js-nolint
getKey(key)
```

### Parameters

- `key`
  - : کلید یا بازهٔ کلیدی که رکورد مورد نظر برای بازیابی را مشخص می‌کند.

### Return value

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مرتبط با این عملیات روی آن fire می‌شوند. اگر عملیات موفق باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست، کلید اولین رکوردی است که با کلید یا بازهٔ کلیدی داده‌شده مطابقت دارد.

### Exceptions

این متد ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر را پرتاب کند:

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("IDBObjectStore")}} حذف یا پاک شده باشد، پرتاب می‌شود.
- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این {{domxref("IDBObjectStore")}} غیرفعال باشد، پرتاب می‌شود.
- `DataError` {{domxref("DOMException")}}
  - : اگر کلید یا بازهٔ کلیدی ارائه‌شده شامل یک کلید نامعتبر باشد، پرتاب می‌شود.

## Example

```js
let openRequest = indexedDB.open("telemetry");
openRequest.onsuccess = (event) => {
  let db = event.target.result;
  let store = db.transaction("net-logs").objectStore("net-logs");

  let today = new Date();
  let yesterday = new Date(today);
  yesterday.setDate(today.getDate() - 1);
  let request = store.getKey(IDBKeyRange(yesterday, today));
  request.onsuccess = (event) => {
    let when = event.target.result;
    alert(`The 1st activity in last 24 hours was occurred at ${when}`);
  };
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم یک بازه از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و اعمال تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).