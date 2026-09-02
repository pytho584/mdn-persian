---
title: "IDBFactory: cmp() method"
short-title: cmp()
slug: Web/API/IDBFactory/cmp
page-type: web-api-instance-method
browser-compat: api.IDBFactory.cmp
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`cmp()`** از رابط {{domxref("IDBFactory")}} دو مقدار را به‌عنوان کلید مقایسه می‌کند تا برابری و ترتیب را برای عملیات IndexedDB، مانند ذخیره‌سازی و پیمایش، تعیین کند.

> [!NOTE]
> از این متد برای مقایسه مقادیر دلخواه جاوااسکریپت استفاده نکنید؛ زیرا بسیاری از مقادیر جاوااسکریپت یا کلیدهای معتبر IndexedDB نیستند (مانند بولین‌ها و اشیا) یا به‌عنوان کلیدهای هم‌ارز IndexedDB در نظر گرفته می‌شوند. برای مثال، IndexedDB ویژگی‌های غیرعددی آرایه‌ها را نادیده می‌گیرد و آن‌ها را به‌عنوان آرایه‌های خالی در نظر می‌گیرد؛ بنابراین هر آرایه‌ای که ویژگی غیرعددی داشته باشد، هم‌ارز با دیگر آرایه‌های غیرعددی تلقی می‌شود. اگر هر یک از مقادیر کلید معتبر نباشد، این متد یک استثنا صادر می‌کند.

## Syntax

```js-nolint
cmp(first, second)
```

### پارامترها

- `first`
  - : اولین کلیدی که باید مقایسه شود.
- `second`
  - : دومین کلیدی که باید مقایسه شود.

### مقدار بازگشتی

یک عدد صحیح که نتیجه مقایسه را نشان می‌دهد؛ جدول زیر مقادیر ممکن و معنی آن‌ها را فهرست می‌کند:

| مقدار بازگشتی | توضیح                              |
| -------------- | ----------------------------------- |
| -1             | کلید اول کوچک‌تر از کلید دوم است    |
| 0              | کلید اول برابر با کلید دوم است      |
| 1              | کلید اول بزرگ‌تر از کلید دوم است    |

### استثناها

- `DataError` {{domxref("DOMException")}}
  - : اگر یکی از کلیدهای ارائه‌شده کلید معتبری نباشد، پرتاب می‌شود.

## مثال‌ها

```js
const a = 1;
const b = 2;
const result = window.indexedDB.cmp(a, b);
console.log(`Comparison results: ${result}`);
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
- بازیابی و اعمال تغییرات روی داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از کرسرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).