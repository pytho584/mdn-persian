---
title: "Document: adoptedStyleSheets property"
short-title: adoptedStyleSheets
slug: Web/API/Document/adoptedStyleSheets
page-type: web-api-instance-property
browser-compat: api.Document.adoptedStyleSheets
---

{{APIRef("CSSOM")}}

ویژگی **`adoptedStyleSheets`** در رابط {{domxref("Document")}} برای تنظیم آرایه‌ای از استایل‌شیت‌های ساخته‌شده (constructed stylesheets) استفاده می‌شود که قرار است توسط سند به کار گرفته شوند.

> [!NOTE]
> استایل‌شیت ساخته‌شده (constructed stylesheet) یک استایل‌شیت است که به‌صورت برنامه‌نویسی و با استفاده از [سازندهٔ `CSSStyleSheet()`](/en-US/docs/Web/API/CSSStyleSheet/CSSStyleSheet) ایجاد می‌شود (در مقایسه با استایل‌شیتی که توسط عامل کاربر هنگام وارد کردن یک استایل‌شیت از یک اسکریپت ایجاد می‌شود، یا استایل‌شیتی که با استفاده از {{HTMLElement('style')}} و {{CSSXref('@import')}} وارد می‌شود، یا از طریق {{HTMLElement('link')}} پیوند داده می‌شود).

همچنین می‌توان همان استایل‌شیت‌های ساخته‌شده را با استفاده از ویژگی [`ShadowRoot.adoptedStyleSheets`](/en-US/docs/Web/API/ShadowRoot/adoptedStyleSheets) با یک یا چند نمونهٔ {{domxref("ShadowRoot")}} به اشتراک گذاشت.
تغییر در یک استایل‌شیت پذیرفته‌شده (adopted) بر تمام اشیایی که آن را پذیرفته‌اند تأثیر می‌گذارد.

استایل‌شیت‌های موجود در این ویژگی همراه با سایر استایل‌شیت‌های سند و با استفاده از [الگوریتم آبشاری CSS](/en-US/docs/Web/CSS/Guides/Cascade/Introduction) ارزیابی می‌شوند.
در مواردی که ترتیب استایل‌شیت‌ها در تعیین قواعد مورد توجه قرار می‌گیرد، فرض بر این است که `adoptedStyleSheets` پس از استایل‌شیت‌های موجود در [`Document.styleSheets`](/en-US/docs/Web/API/Document/styleSheets) مرتب می‌شوند.

فقط استایل‌شیت‌هایی را می‌توان پذیرفت که با استفاده از [سازندهٔ `CSSStyleSheet()`](/en-US/docs/Web/API/CSSStyleSheet/CSSStyleSheet) در بافت (context) {{domxref("Document")}} جاری ساخته شده باشند.

## Value

مقدار (Value) یک آرایه از نمونه‌های {{domxref("CSSStyleSheet")}} است که باید با استفاده از سازندهٔ {{domxref("CSSStyleSheet.CSSStyleSheet()", "CSSStyleSheet()")}} در بافت همان {{domxref("Document")}} ساخته شده باشند.

اگر نیاز به تغییر آرایه بود، از تغییرات درجا (in-place) مانند `push()` استفاده کنید. خود نمونه‌های {{domxref("CSSStyleSheet")}} نیز قابل تغییر هستند و این تغییرات در هر جایی که استایل‌شیت پذیرفته شده باشد اعمال می‌شوند.

در نسخهٔ قبلی مشخصات، آرایه قابل تغییر نبود؛ بنابراین تنها راه افزودن استایل‌شیت‌های جدید، تخصیص یک آرایهٔ جدید به `adoptedStyleSheets` بود.

### Exceptions

- `NotAllowedError` {{domxref("DOMException")}}
  - : یکی از نمونه‌های {{domxref("CSSStyleSheet")}} در آرایه با استفاده از [سازندهٔ `CSSStyleSheet()`](/en-US/docs/Web/API/CSSStyleSheet/CSSStyleSheet) ساخته نشده بود، یا در سندی غیر از سند جاری (مانند سندی در یک frame) ایجاد شده بود.

## Examples

### پذیرش یک استایل‌شیت

کد زیر ساخت یک استایل‌شیت را نشان می‌دهد و سپس {{domxref("CSSStyleSheet.replaceSync()")}} را برای افزودن یک قانون به آن فراخوانی می‌کند.
سپس استایل‌شیت به یک آرایه اضافه شده و به ویژگی `adoptedStyleSheets` اختصاص داده می‌شود.

```js
// Create an empty "constructed" stylesheet
const sheet = new CSSStyleSheet();
// Apply a rule to the sheet
sheet.replaceSync("a { color: red; }");

// Apply the stylesheet to a document
document.adoptedStyleSheets.push(sheet);
```

می‌توانیم با استفاده از {{domxref("CSSStyleSheet.insertRule()")}} قانون جدیدی به استایل‌شیت اضافه کنیم.

```js
sheet.insertRule("* { background-color: blue; }");
// The document will now have blue background.
```

### اشتراک‌گذاری یک استایل‌شیت با shadow DOM

می‌توانیم یک استایل‌شیت را به روشی مشابه با یک shadow root به اشتراک بگذاریم.

```js
// Create an element in the document and then create a shadow root:
const node = document.createElement("div");
const shadow = node.attachShadow({ mode: "open" });

// Adopt the same sheet into the shadow DOM
shadow.adoptedStyleSheets = [sheet];
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## همچنین ببینید

- [Constructable Stylesheets](https://web.dev/articles/constructable-stylesheets) (web.dev)
- [Using the Shadow DOM](/en-US/docs/Web/API/Web_components/Using_shadow_DOM)
- [`CSSStyleSheet()` constructor](/en-US/docs/Web/API/CSSStyleSheet/CSSStyleSheet)
- {{domxref("CSSStyleSheet.replaceSync()")}}
- {{domxref("CSSStyleSheet.replace()")}}
- {{domxref("CSSStyleSheet.insertRule()")}}
- {{domxref("CSSStyleSheet.deleteRule()")}}