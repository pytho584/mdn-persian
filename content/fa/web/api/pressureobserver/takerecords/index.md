---
title: "PressureObserver: takeRecords() method"
---

---
title: "PressureObserver: takeRecords() method"
short-title: takeRecords()
slug: Web/API/PressureObserver/takeRecords
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PressureObserver.takeRecords
---

{{APIRef("Compute Pressure API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_service")}}{{securecontext_header}}

متد **`takeRecords()`** از رابط {{domxref('PressureObserver')}} فهرست فعلیِ سوابق فشار ذخیره‌شده در ناظر فشار را بازمی‌گرداند و آن را خالی می‌کند.

این متد زمانی مفید است که می‌خواهید مشاهده یک منبع را متوقف کنید، اما مطمئن شوید که همه رکوردهایی را که هنوز به callback ناظر ارسال نشده‌اند، دریافت کرده‌اید.

## نحو

```js-nolint
takeRecords()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Array")}} شامل اشیاء {{domxref("PressureRecord")}}.

## نمونه‌ها

### برداشتن سوابق

در مثال زیر، فهرست فعلیِ سوابق فشار در `records` ذخیره و ناظر فشار خالی می‌شود.

```js
const observer = new PressureObserver(callback);
observer.observe("cpu");

const records = observer.takeRecords();
observer.disconnect(); // shut down observer now that we've taken records

if (records.length > 0) {
  console.log(records[0].state);
  console.log(records[0].time);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}