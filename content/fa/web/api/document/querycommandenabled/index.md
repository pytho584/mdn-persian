---
title: "Document: queryCommandEnabled() method"
---

---
title: "Document: queryCommandEnabled() method"
short-title: queryCommandEnabled()
slug: Web/API/Document/queryCommandEnabled
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.Document.queryCommandEnabled
---

{{ApiRef("DOM")}}{{deprecated_header}}{{Non-standard_header}}

> [!NOTE]
> اگرچه متد {{domxref("Document/execCommand", "execCommand()")}} منسوخ شده است، اما اگر بنا به دلایلی که در همان صفحه ذکر شده تصمیم به استفاده از آن گرفتید، بهتر است برای اطمینان از سازگاری، در دسترس بودن دستور را با استفاده از `queryCommandEnabled()` بررسی کنید.

متد **`Document.queryCommandEnabled()`** مشخص می‌کند که آیا دستور ویرایشگر مشخص‌شده توسط مرورگر فعال است یا نه.

## سینتکس

```js-nolint
queryCommandEnabled(command)
```

### پارامترها

- `command`
  - : دستوری که باید تعیین شود آیا از آن پشتیبانی می‌شود یا نه.

### مقدار بازگشتی

یک مقدار بولی برمی‌گرداند که اگر دستور فعال باشد `true` و اگر فعال نباشد `false` است.

## نکات

- برای دستورهای `"cut"` و `"copy"`، این متد فقط زمانی `true` برمی‌گرداند که از یک زمینه اجرایی (thread) ایجادشده توسط کاربر فراخوانی شود.
- دستور `"paste"` نه‌تنها وقتی `false` برمی‌گرداند که قابلیت مربوطه در دسترس نباشد، بلکه وقتی اسکریپت فراخوانی‌کننده مجوزهای کافی برای انجام عمل را نداشته باشد نیز `false` برمی‌گرداند.

## مثال

```js
const flg = document.queryCommandEnabled("SelectAll");

if (flg) {
  document.execCommand("SelectAll", false, null); // command is enabled, run it
}
```

## مشخصات

این قابلیت بخشی از هیچ مشخصات فعلی نیست و دیگر در مسیر تبدیل شدن به یک استاندارد قرار ندارد. یک [پیش‌نویس غیررسمی مشخصات W3C برای execCommand](https://w3c.github.io/editing/docs/execCommand/) وجود دارد.

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("document.execCommand()")}}
- {{domxref("document.queryCommandSupported()")}}