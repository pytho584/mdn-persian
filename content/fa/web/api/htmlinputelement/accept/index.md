---
title: "HTMLInputElement: accept property"
short-title: accept
slug: Web/API/HTMLInputElement/accept
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.accept
---

{{ApiRef("HTML DOM")}}

خاصیت **`accept`** از رابط {{domxref("HTMLInputElement")}} منعکس‌کنندهٔ صفت [`accept`](/en-US/docs/Web/HTML/Reference/Elements/input#accept) عنصر {{HTMLElement("input")}} است. این صفت معمولاً یک فهرست جدا شده با کاما از مشخص‌کننده‌های منحصر‌به‌فرد نوع فایل است که راهنمایی برای نوع فایل مورد انتظار در یک [`<input>` از نوع `file`](/en-US/docs/Web/HTML/Reference/Elements/input/file) فراهم می‌کند. اگر صفت به‌طور صریح تنظیم نشده باشد، خاصیت `accept` یک رشتهٔ خالی خواهد بود.

## مقدار

یک رشته که مقدار `accept` عنصر را نمایش می‌دهد، یا یک رشتهٔ خالی در صورتی که هیچ `accept`ای به‌طور صریح تنظیم نشده باشد.

## مثال

```js
const inputElement = document.querySelector("#time");
console.log(inputElement.accept); // مقدار فعلی صفت accept
inputElement.accept = ".doc,.docx,.xml,application/msword"; // تنظیم مقدار accept
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLInputElement.type")}}
- {{domxref("HTMLInputElement.multiple")}}
- {{domxref("HTMLInputElement.capture")}}
- [مشخص‌کننده‌های نوع فایل](/en-US/docs/Web/HTML/Reference/Elements/input/file#unique_file_type_specifiers)
- [استفاده از فایل‌ها در برنامه‌های وب](/en-US/docs/Web/API/File_API/Using_files_from_web_applications)
- [File API](/en-US/docs/Web/API/File_API)