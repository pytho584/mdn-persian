---
title: "Document: getElementById() method"
short-title: getElementById()
slug: Web/API/Document/getElementById
page-type: web-api-instance-method
browser-compat: api.Document.getElementById
---

{{ ApiRef("DOM") }}

متد **`getElementById()`** از رابط {{domxref("Document")}} یک شیء {{domxref("Element")}} برمی‌گرداند که نمایانگر عنصری است که ویژگی {{domxref("Element.id", "id")}} آن با رشته مشخص‌شده مطابقت دارد. از آنجایی که شناسه‌های عناصر در صورت تعریف باید یکتا باشند، این روش راهی مفید برای دسترسی سریع به یک عنصر خاص است.

اگر نیاز به دسترسی به عنصری دارید که شناسه ندارد، می‌توانید از {{domxref("Document.querySelector", "querySelector()")}} برای یافتن عنصر با استفاده از هر {{Glossary("CSS selector", "انتخاب‌گر")}} استفاده کنید.

> **نکته:** شناسه‌ها باید در یک سند یکتا باشند. اگر دو یا چند عنصر در یک سند دارای شناسه یکسان باشند، این متد اولین عنصر یافت‌شده را برمی‌گرداند.

## نحو (Syntax)

```js-nolint
getElementById(id)
```

> **نکته:** حروف بزرگ و کوچک `"Id"` در نام این متد _باید_ برای عملکرد کد صحیح باشد؛ `getElementByID()` _معتبر نیست_ و کار نخواهد کرد، هرچند که طبیعی به نظر برسد.

### پارامترها

- `id`
  - : شناسه عنصر مورد نظر برای مکان‌یابی. شناسه یک رشته حساس به حروف بزرگ و کوچک است که درون سند یکتا است؛ تنها یک عنصر باید دارای هر شناسه مشخصی باشد.

### مقدار بازگشتی

یک شیء {{domxref("Element")}} که عنصر DOM منطبق با شناسه مشخص‌شده را توصیف می‌کند، یا اگر هیچ عنصر منطبقی در سند یافت نشود، `null` برمی‌گرداند.

## مثال‌ها

### HTML

```html
<p id="para">متن اینجا</p>
<button>blue</button>
<button>red</button>
```

### JavaScript

```js
function changeColor(newColor) {
  const elem = document.getElementById("para");
  elem.style.color = newColor;
}

document.querySelectorAll("button").forEach((button) => {
  button.addEventListener("click", (event) => {
    changeColor(event.target.textContent.toLowerCase());
  });
});
```

### نتیجه

{{ EmbedLiveSample('Examples', 250, 120) }}

## نکات استفاده

برخلاف برخی روش‌های دیگر جستجوی عناصر مانند {{domxref("Document.querySelector()")}} و {{domxref("Document.querySelectorAll()")}}، `getElementById()` تنها به عنوان متدی از شیء سراسری `document` در دسترس است و _نه_ به عنوان متدی بر روی تمام اشیاء عنصر در DOM. از آنجایی که مقادیر شناسه باید در کل سند یکتا باشند، نیازی به نسخه‌های «محلی» این تابع نیست.

### مثال

```html
<div id="parent-id">
  <p>سلام دنیا ۱</p>
  <p id="test1">سلام دنیا ۲</p>
  <p>سلام دنیا ۳</p>
  <p>سلام دنیا ۴</p>
</div>
```

```js
const parentDOM = document.getElementById("parent-id");
const test1 = parentDOM.getElementById("test1");
```

اگر هیچ عنصری با `id` داده‌شده وجود نداشته باشد، این تابع `null` برمی‌گرداند. توجه داشته باشید که پارامتر `id` به حروف بزرگ و کوچک حساس است، بنابراین `document.getElementById("Main")` به جای عنصر `<div id="main">` مقدار `null` را برمی‌گرداند، زیرا "M" و "m" برای اهداف این متد متفاوت هستند.

عناصری که در سند نیستند توسط `getElementById()` جستجو نمی‌شوند. هنگام ایجاد یک عنصر و اختصاص یک شناسه به آن، باید عنصر را با {{domxref("Node.insertBefore()")}} یا روشی مشابه در درخت سند وارد کنید تا بتوانید با `getElementById()` به آن دسترسی پیدا کنید:

```js
const element = document.createElement("div");
element.id = "test";
const el = document.getElementById("test"); // el برابر null خواهد بود!
```

در اسناد غیر HTML، پیاده‌سازی DOM باید اطلاعاتی در مورد اینکه کدام ویژگی‌ها از نوع ID هستند داشته باشد. ویژگی‌های با نام "id" از نوع ID نیستند مگر اینکه در DTD سند چنین تعریف شده باشند. ویژگی `id` در موارد رایج [XHTML](/en-US/docs/Glossary/XHTML)، XUL و موارد دیگر به عنوان نوع ID تعریف شده است. پیاده‌سازی‌هایی که نمی‌دانند آیا ویژگی‌ها از نوع ID هستند یا خیر، انتظار می‌رود که `null` را برگردانند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- مرجع {{domxref("Document")}} برای سایر روش‌ها و ویژگی‌هایی که می‌توانید برای دریافت ارجاع به عناصر در سند استفاده کنید.
- {{domxref("Document.querySelector()")}} برای انتخاب‌گرها از طریق پرس‌وجوهایی مانند `'div.myclass'`
- {{domxref("Document.evaluate()")}} - دارای یک روش کاربردی برای انتخاب با `xml:id` در اسناد {{glossary("XML")}}