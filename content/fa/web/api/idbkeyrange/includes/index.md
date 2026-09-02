```
---
title: "IDBKeyRange: includes() method"
---

---
title: "IDBKeyRange: includes() method"
short-title: includes()
slug: Web/API/IDBKeyRange/includes
page-type: web-api-instance-method
browser-compat: api.IDBKeyRange.includes
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد `includes()` از رابط {{domxref("IDBKeyRange")}} یک مقدار بولین برمی‌گرداند که نشان می‌دهد آیا کلید مشخص‌شده درون بازه کلید قرار دارد یا نه.

## نحو

```js-nolint
includes(key)
```

### پارامترها

- `key`
  - : کلیدی که می‌خواهید وجود آن را در بازه کلید بررسی کنید. این مقدار می‌تواند از هر نوعی باشد.

### مقدار بازگشتی

یک مقدار بولین.

### استثناها

- `DataError` {{domxref("DOMException")}}
  - : اگر کلید ارائه‌شده یک کلید معتبر نباشد، این خطا پرتاب می‌شود.

## مثال‌ها

```js
const keyRangeValue = IDBKeyRange.bound("A", "K", false, false);

keyRangeValue.includes("F");
// Returns true

keyRangeValue.includes("W");
// Returns false
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
- بازیابی و اعمال تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها (cursors): {{domxref("IDBCursor")}}
- مثال مرجع: [اعلان‌های کارها](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
```