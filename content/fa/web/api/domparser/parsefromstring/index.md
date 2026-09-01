---
title: "DOMParser: parseFromString() method"
short-title: parseFromString()
slug: Web/API/DOMParser/parseFromString
page-type: web-api-instance-method
browser-compat: api.DOMParser.parseFromString
---

{{APIRef("DOMParser")}}

> [!WARNING]
> این متد ورودی خود را به عنوان HTML تجزیه می‌کند و نتیجه را در DOM می‌نویسد. APIهایی مانند این به عنوان [injection sinks](/en-US/docs/Web/API/Trusted_Types_API#concepts_and_usage) شناخته می‌شوند و در صورت اصلیت داشتن ورودی از طرف مهاجم، می‌توانند بستری برای حملات [cross-site scripting (XSS)](/en-US/docs/Web/Security/Attacks/XSS) باشند.
>
> می‌توانید این خطر را با همیشه ارسال اشیاء `TrustedHTML` به جای رشته‌ها و [اجباری کردن trusted types](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) کاهش دهید.
> برای اطلاعات بیشتر به [ملاحظات امنیتی](#security_considerations) مراجعه کنید.

متد **`parseFromString()`** از رابط {{domxref("DOMParser")}} یک ورودی حاوی HTML یا XML را تجزیه می‌کند و یک {{domxref("Document")}} با نوع مشخص‌شده در ویژگی {{domxref("Document/contentType","contentType")}} برمی‌گرداند.

> [!NOTE]
> متد استاتیک [`Document.parseHTMLUnsafe()`](/en-US/docs/Web/API/Document/parseHTMLUnsafe_static) یک جایگزین ارگونومیک برای تجزیه نشانه‌گذاری HTML به یک {{domxref("Document")}} فراهم می‌کند.

## Syntax

```js-nolint
parseFromString(input, mimeType)
```

### Parameters

- `input`
  - : یک نمونه از {{domxref("TrustedHTML")}} یا یک رشته که HTML مورد نظر برای تجزیه را تعریف می‌کند. نشانه‌گذاری باید حاوی یک سند {{Glossary("HTML")}}، {{Glossary("XML")}}، {{Glossary("XHTML")}} یا {{Glossary("SVG")}} باشد.
- `mimeType`
  - : یک رشته که مشخص می‌کند از تجزیه‌کننده XML یا تجزیه‌کننده HTML برای تجزیه رشته استفاده شود. مقادیر مجاز عبارتند از:
    - `text/html`
    - `text/xml`
    - `application/xml`
    - `application/xhtml+xml`
    - `image/svg+xml`

### Return value

یک {{domxref("Document")}} با {{domxref("Document/contentType","contentType")}} مطابق با `mimeType` داده شده.

> [!NOTE]
> ممکن است مرورگر در واقع یک شیء {{domxref("HTMLDocument")}} یا {{domxref("XMLDocument")}} برگرداند. این‌ها از {{domxref("Document")}} مشتق شده‌اند و هیچ ویژگی اضافه نمی‌کنند: اساساً معادل هستند.

### Exceptions

- [`TypeError`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypeError)
  - : این خطا زمانی پرتاب می‌شود که:
    - `mimeType` مقداری دریافت کند که جزو [مقادیر مجاز](#mimetype) نباشد.
    - `input` به عنوان یک رشته مقداردهی شود در حالی که [Trusted Types](/en-US/docs/Web/API/Trusted_Types_API) توسط [CSP اجباری شده](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) و هیچ سیاست پیش‌فرضی تعریف نشده باشد.

## Description

متد **`parseFromString()`** یک ورودی حاوی HTML یا XML را تجزیه می‌کند و یک {{domxref("Document")}} با {{domxref("Document/contentType","contentType")}} مطابق با `mimeType` برمی‌گرداند. این `Document` شامل یک DOM کامل درون حافظه است که از سند اصلی در صفحه مرتبط جدا است.

اگر `mimeType` برابر با `text/html` باشد، ورودی به عنوان HTML تجزیه می‌شود و عناصر {{htmlelement("script")}} به عنوان غیرقابل اجرا علامت‌گذاری می‌شوند، رویدادها شلیک نمی‌شوند، و کنترل‌کننده‌های رویداد برای اجرای اسکریپت‌های درون خطی فراخوانی نمی‌شوند. در حالی که سند می‌تواند منابع مشخص‌شده در عناصر {{htmlelement("iframe")}} و {{htmlelement("img")}} را دانلود کند، اساساً خنثی (inert) است. این مفید است زیرا می‌توانید ورودی‌های HTML شامل {{glossary("Shadow tree","declarative shadow roots")}} را تجزیه کنید و عملیات‌هایی روی سند انجام دهید بدون اینکه روی صفحه قابل مشاهده تأثیر بگذارید. به عنوان مثال، می‌توانید از این برای پالایش (sanitize) درخت ورودی استفاده کنید و در صورت نیاز بخش‌هایی از ورودی را به DOM قابل مشاهده تزریق کنید.

برای سایر مقادیر مجاز (`text/xml`، `application/xml`، `application/xhtml+xml` و `image/svg+xml`) ورودی به عنوان XML تجزیه می‌شود. این در صورتی مفید است که می‌خواهید فایل‌های XML را وارد کنید، ساختار آن‌ها را اعتبارسنجی کنید و داده‌ها را استخراج کنید. اگر ورودی یک XML خوش‌فرم (well-formed) نباشد، سند برگشتی حاوی یک گره `<parsererror>` خواهد بود که ماهیت خطای تجزیه را توصیف می‌کند.

مقادیر غیرمجاز `mimeType` باعث پرتاب [`TypeError`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypeError) می‌شوند.

### Security considerations

این متد ورودی خود را به یک DOM جداگانه درون حافظه تجزیه می‌کند، هر عنصر {{htmlelement("script")}} را غیرفعال می‌کند و از اجرای کنترل‌کننده‌های رویداد جلوگیری می‌کند. در حالی که سند برگشتی عملاً خنثی (inert) است، کنترل‌کننده‌های رویداد و اسکریپت‌های موجود در DOM آن در صورت درج شدن در DOM قابل مشاهده، قادر به اجرا خواهند بود. بنابراین این متد یک بستر احتمالی برای حملات [cross-site scripting (XSS)](/en-US/docs/Web/Security/Attacks/XSS) است، جایی که ورودی بالقوه ناامن ابتدا بدون پالایش (sanitize) به یک `Document` تجزیه می‌شود و سپس به DOM قابل مشاهده/فعال تزریق می‌شود که در آن کد می‌تواند اجرا شود.

شما باید این خطر را با همیشه ارسال اشیاء {{domxref("TrustedHTML")}} به جای رشته‌ها و [اجباری کردن trusted types](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) با استفاده از دستورالعمل CSP [`require-trusted-types-for`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/require-trusted-types-for) کاهش دهید. این تضمین می‌کند که ورودی از یک تابع تبدیل عبور داده می‌شود که فرصت [پالایش (sanitize)](/en-US/docs/Web/Security/Attacks/XSS#sanitization) ورودی را برای حذف نشانه‌گذاری بالقوه خطرناک (مانند عناصر {{htmlelement("script")}} و ویژگی‌های کنترل‌کننده رویداد) قبل از تزریق دارد.

استفاده از `TrustedHTML` امکان ممیزی و بررسی مؤثر بودن کد پالایش را تنها در چند مکان فراهم می‌کند، به جای اینکه در تمام sinkهای تزریق پراکنده باشد. هنگام استفاده از `TrustedHTML` نیازی به ارسال یک پالاینده (sanitizer) به متد ندارید.

توجه داشته باشید که حتی اگر ورودی عناصر و ویژگی‌هایی را که می‌توانند کد اجرا کنند پالایش کنید، همچنان باید هنگام دریافت هر گونه ورودی کاربر محتاط باشید. به عنوان مثال، صفحه شما ممکن است از داده‌های موجود در یک سند XML برای واکشی فایل‌هایی استفاده کند که سپس اجرا می‌کند.

## Examples

### Parsing an input using Trusted Types

در این مثال، یک ورودی HTML بالقوه مضر را به طور ایمن تجزیه کرده و سپس آن را به DOM صفحه قابل مشاهده تزریق می‌کنیم.

برای کاهش خطر XSS، یک شیء `TrustedHTML` از رشته حاوی HTML ایجاد می‌کنیم. Trusted types هنوز در همه مرورگرها پشتیبانی نمی‌شوند، بنابراین ابتدا [trusted types tinyfill](/en-US/docs/Web/API/Trusted_Types_API#trusted_types_tinyfill) را تعریف می‌کنیم. این به عنوان یک جایگزین شفاف برای API جاوااسکریپت trusted types عمل می‌کند:

```js
if (typeof trustedTypes === "undefined")
  trustedTypes = { createPolicy: (n, rules) => rules };
```

سپس یک {{domxref("TrustedTypePolicy")}} ایجاد می‌کنیم که یک {{domxref("TrustedTypePolicy/createHTML", "createHTML()")}} برای تبدیل رشته ورودی به نمونه‌های {{domxref("TrustedHTML")}} تعریف می‌کند. معمولاً پیاده‌سازی‌های `createHTML()` از کتابخانه‌ای مانند [DOMPurify](https://github.com/cure53/DOMPurify) برای پالایش (sanitize) ورودی استفاده می‌کنند، همانطور که در زیر نشان داده شده است:

```js
const policy = trustedTypes.createPolicy("my-policy", {
  createHTML: (input) => DOMPurify.sanitize(input),
});
```

سپس از این شیء `policy` برای ایجاد یک شیء `TrustedHTML` از رشته ورودی بالقوه ناامن استفاده کرده و آن را به یک `Document` تجزیه می‌کنیم. توجه داشته باشید که `Document` حاصل یک سند HTML کامل با ریشه `<html>`، `<head>` و `<body>` را نشان می‌دهد، حتی اگر ورودی این عناصر را نداشته باشد:

```js
// رشته بالقوه مخرب
const untrustedString = "<p>I might be XSS</p><img src='x' onerror='alert(1)'>";

// ایجاد یک نمونه TrustedHTML با استفاده از policy
const trustedHTML = policy.createHTML(untrustedString);

// تجزیه TrustedHTML (که حاوی یک رشته قابل اعتماد است)
const safeDocument = parser.parseFromString(trustedHTML, "text/html");
```

اکنون `safeDocument` شامل یک DOM است که طبق policy ما از عناصر مضر پالایش شده است. در زیر از {{domxref("Element.replaceWith()")}} برای جایگزینی `body` DOM قابل مشاهده با body سند خود استفاده می‌کنیم: اسکریپت‌های موجود در body جدید اجرا خواهند شد، همچنین کدهای موجود در کنترل‌کننده‌های رویداد هنگام فعال شدن اجرا می‌شوند.

```js
document.body.replaceWith(safeDocument.body);
```

### Parsing XML, SVG, and HTML

کد زیر نحوه استفاده از متد برای تجزیه هر یک از انواع محتوا را نشان می‌دهد. در حالی که باید در کد واقعی از trusted types استفاده کنید، در اینجا برای اختصار از آن‌ها صرف‌نظر شده است.

```js
const parser = new DOMParser();

const xmlString = "<warning>Beware of the tiger</warning>";
const doc1 = parser.parseFromString(xmlString, "application/xml");
console.log(doc1.contentType); // "application/xml"

const svgString = '<circle cx="50" cy="50" r="50"/>';
const doc2 = parser.parseFromString(svgString, "image/svg+xml");
console.log(doc2.contentType); // "image/svg+xml"

const htmlString = "<strong>Beware of the leopard</strong>";
const doc3 = parser.parseFromString(htmlString, "text/html");
console.log(doc3.contentType); // "text/html"

console.log(doc1.documentElement.textContent);
// "Beware of the tiger"

console.log(doc2.firstChild.tagName);
// "circle"

console.log(doc3.body.firstChild.textContent);
// "Beware of the leopard"
```

توجه داشته باشید که انواع MIME `application/xml` و `image/svg+xml` در بالا از نظر عملکردی یکسان هستند - دومی شامل هیچ قانون تجزیه خاص SVG نیست.

### Error handling

هنگام استفاده از تجزیه‌کننده XML با رشته‌ای که یک XML خوش‌فرم (well-formed) را نشان نمی‌دهد، {{domxref("XMLDocument")}} برگشتی توسط `parseFromString` حاوی یک گره `<parsererror>` خواهد بود که ماهیت خطای تجزیه را توصیف می‌کند.

```js
const parser = new DOMParser();

const xmlString = "<warning>Beware of the missing closing tag";
const doc = parser.parseFromString(xmlString, "application/xml");
const errorNode = doc.querySelector("parsererror");
if (errorNode) {
  // تجزیه ناموفق بود
} else {
  // تجزیه موفقیت‌آمیز بود
}
```

علاوه بر این، خطای تجزیه ممکن است در کنسول جاوااسکریپت مرورگر گزارش شود.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("XMLSerializer")}}
- {{jsxref("JSON.parse()")}} - معادل برای اسناد {{jsxref("JSON")}}.