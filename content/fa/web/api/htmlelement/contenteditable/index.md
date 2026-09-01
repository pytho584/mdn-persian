---
title: "HTMLElement: contentEditable property"
short-title: contentEditable
slug: Web/API/HTMLElement/contentEditable
page-type: web-api-instance-property
browser-compat: api.HTMLElement.contentEditable
---

{{APIRef("HTML DOM")}}

ویژگی **`contentEditable`** در رابط {{domxref("HTMLElement")}} مشخص می‌کند که آیا عنصر قابل ویرایش است یا خیر.

این ویژگی شمارشی (enumerated) می‌تواند مقادیر زیر را داشته باشد:

- `"true"` نشان می‌دهد که عنصر `contenteditable` است.
- `"false"` نشان می‌دهد که عنصر قابل ویرایش نیست.
- `"plaintext-only"` نشان می‌دهد که متن خام عنصر قابل ویرایش است، اما قالب‌بندی متن غنی (rich text) غیرفعال است.

می‌توانید از ویژگی {{domxref("HTMLElement.isContentEditable")}} برای بررسی مقدار بولی محاسبه‌شده این ویژگی استفاده کنید.

اگر ویژگی وجود نداشته باشد یا مقدار آن نامعتبر باشد، مقدار آن از عنصر والد به ارث برده می‌شود؛ بنابراین عنصر بر اساس عنصر والد قابل ویرایش است (یا نیست).

## مقدار

یک رشته (string).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLElement.isContentEditable")}}
- ویژگی سراسری [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable)