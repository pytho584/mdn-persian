---
title: "HTMLInputElement: capture property"
short-title: capture
slug: Web/API/HTMLInputElement/capture
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.capture
---

{{ApiRef("HTML DOM")}}

خصوصیت **`capture`** در رابط {{domxref("HTMLInputElement")}}، صفت [`capture`](/en-US/docs/Web/HTML/Reference/Attributes/capture) عنصر {{HTMLElement("input")}} را بازتاب می‌دهد. این خصوصیت و صفت فقط برای [`<input>` از نوع `file`](/en-US/docs/Web/HTML/Reference/Elements/input/file) کاربرد دارند و مشخص می‌کنند که آیا یک فایل جدید باید از دوربین یا میکروفونِ رو به کاربر (`user`) یا رو به بیرون (`environment`) گرفته شود. نوع فایل با صفت [`accept`](/en-US/docs/Web/HTML/Reference/Attributes/accept) تعیین می‌شود. اگر صفت به‌صورت صریح تنظیم نشده باشد، خصوصیت `capture` یک رشتهٔ خالی است.

## مقدار

یک رشته؛ معمولاً یا `user` یا `environment`، یا یک رشتهٔ خالی (`\"\"`).

## مثال

```js
const inputElement = document.querySelector("avatar");
console.log(inputElement.capture); // the current value of the capture attribute
inputElement.capture = "user"; // sets the capture value
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLInputElement.type")}}
- {{domxref("HTMLInputElement.multiple")}}
- {{domxref("HTMLInputElement.accept")}}
- {{domxref("HTMLInputElement.files")}}
- [File type specifiers](/en-US/docs/Web/HTML/Reference/Elements/input/file#unique_file_type_specifiers)
- [Using files from web applications](/en-US/docs/Web/API/File_API/Using_files_from_web_applications)
- [File API](/en-US/docs/Web/API/File_API)