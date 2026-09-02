---
title: "IDBKeyRange: lowerOpen property"
---

---
title: "IDBKeyRange: lowerOpen property"
short-title: lowerOpen
slug: Web/API/IDBKeyRange/lowerOpen
page-type: web-api-instance-property
browser-compat: api.IDBKeyRange.lowerOpen
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`lowerOpen`** از رابط {{domxref("IDBKeyRange")}} یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا مقدار کران پایین در محدوده کلید گنجانده شده است یا خیر.

## مقدار

یک مقدار بولی:

| مقدار   | توضیح                                              |
| ------- | ------------------------------------------------------- |
| `true`  | مقدار کران پایین در محدوده کلید گنجانده نشده است. |
| `false` | مقدار کران پایین در محدوده کلید گنجانده شده است.     |

## مثال‌ها

مثال زیر نحوه استفاده از یک محدوده کلید را نشان می‌دهد. در اینجا `keyRangeValue = IDBKeyRange.upperBound("F", "W", true, true);` را تعریف می‌کنیم؛ محدوده‌ای که همه‌چیز بین «F» و «W» را شامل می‌شود، اما خود آن‌ها را شامل نمی‌شود؛ زیرا هر دو کران بالا و پایین به صورت باز (`true`) تعریف شده‌اند. ما یک تراکنش (با استفاده از {{domxref("IDBTransaction")}}) و یک object store باز می‌کنیم و یک Cursor را با {{domxref("IDBObjectStore.openCursor")}} باز می‌کنیم و `keyRangeValue` را به عنوان مقدار اختیاری محدوده کلید آن تعیین می‌کنیم.

پس از تعریف محدوده کلید، مقدار ویژگی `lowerOpen` آن را در کنسول ثبت می‌کنیم؛ انتظار می‌رود مقدار «true» ظاهر شود: کران پایین باز است، بنابراین در محدوده گنجانده نخواهد شد.

> [!NOTE]
> برای یک مثال کامل‌تر که به شما امکان آزمایش با محدوده کلید را می‌دهد، به مخزن [IDBKeyRange-example](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbkeyrange) ما نگاهی بیندازید ([همچنین مثال زنده را ببینید](https://mdn.github.io/dom-examples/indexeddb-examples/idbkeyrange/).)

```js
function displayData() {
  const keyRangeValue = IDBKeyRange.bound("F", "W", true, true);
  console.log(keyRangeValue.lowerOpen);

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
- تنظیم محدوده کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از Cursorها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).