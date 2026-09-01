---
title: "HTMLInputElement: dirName property"
short-title: dirName
slug: Web/API/HTMLInputElement/dirName
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.dirName
---

{{APIRef("HTML DOM")}}

ویژگی **`dirName`** در رابط {{domxref("HTMLInputElement")}} جهت عنصر را مشخص می‌کند و امکان ارسال این مقدار را فراهم می‌سازد. این ویژگی مقدار صفت [`dirName`](/en-US/docs/Web/HTML/Reference/Attributes/dirname) عنصر {{htmlelement("input")}} را بازتاب می‌دهد. این ویژگی قابل خواندن و نوشتن است.

صفت `dirname` فقط برای `<input>`های نوع [`hidden`](/en-US/docs/Web/HTML/Reference/Elements/input/hidden)، [`text`](/en-US/docs/Web/HTML/Reference/Elements/input/text)، [`search`](/en-US/docs/Web/HTML/Reference/Elements/input/search)، [`url`](/en-US/docs/Web/HTML/Reference/Elements/input/url)، [`tel`](/en-US/docs/Web/HTML/Reference/Elements/input/tel) و [`email`](/en-US/docs/Web/HTML/Reference/Elements/input/email) معتبر است و نحوهٔ ارسال جهت عنصر را کنترل می‌کند. وقتی این صفت وجود داشته باشد، کنترل فرم با دو جفت نام/مقدار ارسال می‌شود: اولی جفت [`name`](/en-US/docs/Web/HTML/Reference/Elements/input#name) و [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) خود عنصر، و دومی جفتی که نام آن مقدار صفت [`dirname`](/en-US/docs/Web/HTML/Reference/Elements/input#dirname) است و مقدار آن `ltr` یا `rtl` خواهد بود که توسط مرورگر تعیین می‌شود.

## مقدار

یک رشته (string). جهت عنصر.

## مثال‌ها

```js
inputElement.dirName = "rtl";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTextAreaElement.dirName")}}
- [صفت `dir`](/en-US/docs/Web/HTML/Reference/Global_attributes/dir)
- [ارسال داده‌های فرم](/en-US/docs/Learn_web_development/Extensions/Forms/Sending_and_retrieving_form_data)