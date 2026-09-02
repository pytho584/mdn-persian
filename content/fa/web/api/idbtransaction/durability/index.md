---
title: "IDBTransaction: durability property"
---

---
title: "IDBTransaction: durability property"
short-title: durability
slug: Web/API/IDBTransaction/durability
page-type: web-api-instance-property
browser-compat: api.IDBTransaction.durability
---

{{securecontext_header}}{{APIRef("IndexedDB")}}

خاصیتِ فقط‌خواندنیِ **`durability`** در رابط {{domxref("IDBTransaction")}}، راهنمای دوام (durability hint) را که تراکنش با آن ایجاد شده است برمی‌گرداند. این یک راهنما برای عامل کاربر (user agent) است که هنگام ثبت نهایی (commit) تراکنش، آیا عملکرد را در اولویت قرار دهد یا دوام را.

مقدار این خاصیت در پارامتر [`options.durability`](/en-US/docs/Web/API/IDBDatabase/transaction#options) هنگام ایجاد یک تراکنش با استفاده از {{domxref("IDBDatabase.transaction()")}} تعریف می‌شود.

## مقدار

هر یک از {{jsxref('String', 'strings')}} تحت‌اللفظی زیر:

- `"strict"`
  - : عامل کاربر فقط پس از تأیید اینکه همهٔ تغییراتِ در انتظار با موفقیت روی یک رسانهٔ ذخیره‌سازیِ پایدار نوشته شده‌اند، می‌تواند در نظر بگیرد که تراکنش با موفقیت ثبت نهایی شده است.
- `"relaxed"`
  - : عامل کاربر می‌تواند به محض اینکه همهٔ تغییراتِ در انتظار به سیستم‌عامل نوشته شدند، بدون تأییدِ بیشتر، در نظر بگیرد که تراکنش با موفقیت ثبت نهایی شده است.
- `"default"`
  - : عامل کاربر باید رفتارِ پیش‌فرضِ دوام خود را برای سطل ذخیره‌سازی (storage bucket) به کار گیرد. اگر طور دیگری مشخص نشده باشد، این مقدار برای تراکنش‌ها پیش‌فرض است.

## مثال‌ها

برای یک مثال کامل و قابل اجرا، به برنامهٔ [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) مراجعه کنید ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}