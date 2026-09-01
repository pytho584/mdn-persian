---
title: "Document: queryCommandSupported() method"
short-title: queryCommandSupported()
slug: Web/API/Document/queryCommandSupported
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.Document.queryCommandSupported
---

{{ApiRef("DOM")}}{{deprecated_header}}{{Non-standard_header}}

> [!NOTE]
> اگرچه متد {{domxref("Document/execCommand", "execCommand()")}} منسوخ شده است، اما اگر به دلایلی که در آن صفحه ذکر شده تصمیم به استفاده از آن دارید، بهتر است با استفاده از `queryCommandSupported()` از در دسترس بودن دستور اطمینان حاصل کنید.

متد **`Document.queryCommandSupported()`** گزارش می‌دهد که آیا دستور ویرایشگر مشخص شده توسط مرورگر پشتیبانی می‌شود یا خیر.

## نحو (Syntax)

```js-nolint
queryCommandSupported(command)
```

### پارامترها

- `command`
  - : دستوری که باید مشخص شود آیا پشتیبانی می‌شود یا خیر.

### مقدار بازگشتی

یک مقدار بولی برمی‌گرداند که اگر دستور پشتیبانی شود `true` و در غیر این صورت `false` است.

## نکات

دستور `'paste'` نه تنها در صورت عدم دسترسی به ویژگی، بلکه در صورتی که اسکریپت فراخوانی‌کننده آن مجوز کافی برای انجام عمل را نداشته باشد، `false` برمی‌گرداند.

## مثال‌ها

```js
const flg = document.queryCommandSupported("SelectAll");

if (flg) {
  // Do something…
}
```

## مشخصات

این ویژگی بخشی از هیچ مشخصات فعلی نیست. دیگر در مسیر تبدیل شدن به یک استاندارد نیست. یک پیش‌نویس غیررسمی از [مشخصات execCommand در W3C](https://w3c.github.io/editing/docs/execCommand/) وجود دارد.

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("document.execCommand()")}}
- {{domxref("document.queryCommandEnabled()")}}