---
title: "FormData: FormData() constructor"
short-title: FormData()
slug: Web/API/FormData/FormData
page-type: web-api-constructor
browser-compat: api.FormData.FormData
---

{{APIRef("XMLHttpRequest API")}} {{AvailableInWorkers}}

سازندهٔ **`FormData()`** یک شیء جدید {{domxref("FormData")}} می‌سازد.

## نحو

```js-nolint
new FormData()
new FormData(form)
new FormData(form, submitter)
```

### پارامترها

- `form` {{optional_inline}}
  - : یک عنصر HTML {{HTMLElement("form")}} — وقتی مشخص شود، شیء {{domxref("FormData")}} با کلیدها/مقادیر جاری `form` با استفاده از ویژگی name هر عنصر برای کلیدها و مقدار ارسالی آن‌ها برای مقادیر پر می‌شود. همچنین محتوای ورودی فایل را کدگذاری می‌کند. یک رویداد {{domxref("HTMLFormElement/formdata_event", "formdata")}} روی فرم هنگامی که شیء `FormData` ساخته می‌شود، شلیک می‌شود و به فرم اجازه می‌دهد در صورت نیاز داده‌های فرم را تغییر دهد.
- `submitter` {{optional_inline}}
  - : یک {{Glossary("submit button")}} که عضوی از `form` است. اگر `submitter` دارای ویژگی `name` باشد یا یک `{{HtmlElement('input/image', '&lt;input type="image"&gt;')}}` باشد، داده‌های آن [گنجانده می‌شود](/en-US/docs/Glossary/Submit_button#form_data_entries) در شیء {{domxref("FormData")}} (مثلاً `btnName=btnValue`).

### استثناها

- {{jsxref("TypeError")}}
  - : اگر `submitter` مشخص‌شده یک {{Glossary("submit button", "دکمه ارسال")}} نباشد، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر `submitter` مشخص‌شده عضوی از `form` نباشد، پرتاب می‌شود. `submitter` باید یا از نوادگان عنصر فرم باشد یا دارای ویژگی [`form`](/en-US/docs/Web/HTML/Reference/Elements/input#form) باشد که به فرم اشاره می‌کند.

## مثال‌ها

### ایجاد یک FormData خالی

خط زیر یک شیء {{domxref("FormData")}} خالی می‌سازد:

```js
const formData = new FormData();
```

شما می‌توانید یک جفت کلید/مقدار با استفاده از {{domxref("FormData.append", "append()")}} به آن اضافه کنید:

```js
formData.append("username", "Chris");
```

### پیش‌پر کردن از یک عنصر فرم HTML

شما می‌توانید آرگومان‌های اختیاری `form` و `submitter` را هنگام ایجاد شیء `FormData` مشخص کنید تا آن را با مقادیر فرم مشخص‌شده پیش‌پر کنید.

> [!NOTE]
> فقط کنترل‌های موفق فرم در یک شیء FormData گنجانده می‌شوند، یعنی آن‌هایی که دارای name هستند و در حالت غیرفعال نیستند.

#### HTML

```html
<form id="form">
  <input type="text" name="text1" value="foo" />
  <input type="text" name="text2" value="bar" />
  <input type="text" name="text3" value="baz" />
  <input type="checkbox" name="check" checked disabled />
  <button name="intent" value="save">Save</button>
  <button name="intent" value="saveAsCopy">Save As Copy</button>
</form>

<output id="output"></output>
```

```css hidden
form {
  display: none;
}

output {
  display: block;
  white-space: pre-wrap;
}
```

#### JavaScript

```js
const form = document.getElementById("form");
const submitter = document.querySelector("button[value=save]");
const formData = new FormData(form, submitter);

const output = document.getElementById("output");

for (const [key, value] of formData) {
  output.textContent += `${key}: ${value}\n`;
}
```

#### نتیجه

برای اختصار، عنصر `<form>` از دید پنهان شده است.

{{EmbedLiveSample("prepopulating_from_a_html_form_element", "", 150)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از اشیاء FormData](/en-US/docs/Web/API/XMLHttpRequest_API/Using_FormData_Objects)
- {{HTMLElement("Form")}}