---
title: "HTMLTextAreaElement: dirName property"
short-title: dirName
slug: Web/API/HTMLTextAreaElement/dirName
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.dirName
---

{{APIRef("HTML DOM")}}

ویژگی **`dirName`** از رابط {{domxref("HTMLTextAreaElement")}}، جهت‌دار بودن (directionality) عنصر را مشخص می‌کند. این ویژگی منعکس‌کنندهٔ مقدار صفت [`dirName`](/en-US/docs/Web/HTML/Reference/Attributes/dirname) عنصر {{htmlelement("textarea")}} است. می‌توان این ویژگی را خواند یا تنظیم کرد.

صفت `dirname` نحوهٔ ارسال جهت‌دار بودن عنصر را کنترل می‌کند. هنگامی که این صفت وجود داشته باشد، کنترل فرم با دو جفت نام/مقدار ارسال می‌شود: جفت اول [`name`](/en-US/docs/Web/API/HTMLTextAreaElement/name) و [`value`](/en-US/docs/Web/API/HTMLTextAreaElement/value) عنصر `<textarea>` است، و جفت دوم نام صفت [`dirname`](/en-US/docs/Web/HTML/Reference/Elements/textarea#dirname) به عنوان نام و مقداری برابر با `ltr` یا `rtl` (که توسط مرورگر تعیین می‌شود) خواهد بود.

## مقدار

یک رشته. جهت عنصر.

## مثال‌ها

```js
textareaElement.dirName = "rtl";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLInputElement.dirName")}}
- [`dir` attribute](/en-US/docs/Web/HTML/Reference/Global_attributes/dir)
- [Sending form data](/en-US/docs/Learn_web_development/Extensions/Forms/Sending_and_retrieving_form_data)