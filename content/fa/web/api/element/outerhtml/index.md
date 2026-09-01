---
title: "Element: outerHTML property"
short-title: outerHTML
slug: Web/API/Element/outerHTML
page-type: web-api-instance-property
browser-compat: api.Element.outerHTML
---

{{APIRef("DOM")}}

> [!WARNING]
> این ویژگی، ورودی خود را به‌عنوان HTML تجزیه کرده و نتیجه را در DOM می‌نویسد.
> چنین APIهایی به نام [sink تزریق](/en-US/docs/Web/API/Trusted_Types_API#concepts_and_usage) شناخته می‌شوند و اگر ورودی در ابتدا از طرف یک مهاجم باشد، می‌توانند بردار حمله‌ای برای [اسکریپت‌نویسی بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) باشند.
>
> می‌توانید این ریسک را با اختصاص دادن همیشگی اشیاء `TrustedHTML` به‌جای رشته‌ها و [اجباری کردن types مورد اعتماد](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) کاهش دهید.
> برای اطلاعات بیشتر به [ملاحظات امنیتی](#security_considerations) مراجعه کنید.

ویژگی **`outerHTML`** در رابط {{domxref("Element")}}، مارک‌آپ HTML یا XML مربوط به عنصر و همهٔ فرزندان آن را دریافت یا تنظیم می‌کند و در هر دو حالت، هر {{glossary("shadow tree", "shadow root")}} را نادیده می‌گیرد.

برای دریافت یا تنظیم محتوای درونی یک عنصر، به‌جای آن از ویژگی {{domxref("Element.innerHTML", "innerHTML")}} استفاده کنید.

## مقدار

خواندن این ویژگی، رشته‌ای شامل یک سریال‌سازی HTML از خودِ `element` و همهٔ فرزندان آن برمی‌گرداند.

تنظیم این ویژگی، یا یک شیء {{domxref("TrustedHTML")}} می‌پذیرد یا یک رشته.
ورودی به‌عنوان HTML تجزیه می‌شود و عنصر و همهٔ فرزندان آن را با نتیجهٔ تجزیه جایگزین می‌کند.
وقتی مقدار `null` تنظیم شود، همان `null` به رشتهٔ خالی (`""`) تبدیل می‌شود، بنابراین `element.outerHTML = null` معادل `element.outerHTML = ""` است.

### استثناها

- `NoModificationAllowedError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که تلاش شود `outerHTML` روی عنصری تنظیم شود که فرزند مستقیم یک {{domxref("Document")}} است، مانند {{domxref("Document.documentElement")}}.
- `SyntaxError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که تلاش شود `outerHTML` با ورودی XML نامعتبر (well-formed نبودن) تنظیم شود.
- `TypeError`
  - : زمانی پرتاب می‌شود که ویژگی با یک رشته تنظیم شود در حالی که [Trusted Types](/en-US/docs/Web/API/Trusted_Types_API) با [CSP](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) [اجباری شده‌اند](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) و هیچ خط‌مشی پیش‌فرضی تعریف نشده باشد.

## توضیحات

`outerHTML` یک سریال‌سازی از عنصر را دریافت می‌کند، یا HTML یا XMLای را تنظیم می‌کند که باید تجزیه شود تا عنصر درون والدِ خود جایگزین شود.

اگر عنصر هیچ گره والد نداشته باشد، تنظیم ویژگی `outerHTML` نه خودِ عنصر و نه فرزندانش را تغییر نمی‌دهد.
مثلاً:

```js
const div = document.createElement("div");
div.outerHTML = '<div class="test">test</div>';
console.log(div.outerHTML); // خروجی: "<div></div>"
```

همچنین، اگرچه عنصر در سند جایگزین می‌شود، متغیری که ویژگی `outerHTML` روی آن تنظیم شده است همچنان به عنصر اصلی ارجاع می‌دهد:

```js
const p = document.querySelector("p");
console.log(p.nodeName); // نمایش می‌دهد: "P"
p.outerHTML = "<div>This div replaced a paragraph.</div>";
console.log(p.nodeName); // همچنان "P" است
```

### فرار دادن مقادیر ویژگی‌ها (Escaped attribute values)

مقدار برگشتی برخی مقادیر را در ویژگی‌های HTML فرار (escape) می‌کند.
در اینجا می‌بینیم که کاراکتر `&` فرار شده است:

```js
const anchor = document.createElement("a");
anchor.href = "https://developer.mozilla.org?a=b&c=d";
console.log(anchor.outerHTML); // خروجی: "<a href='https://developer.mozilla.org?a=b&amp;c=d'></a>"
```

بعضی مرورگرها همچنین کاراکترهای `<` و `>` را هنگام ظاهر شدن در مقادیر ویژگی‌ها به صورت `&lt;` و `&gt;` سریال‌سازی می‌کنند (به [سازگاری مرورگر](#browser_compatibility) مراجعه کنید).
این کار برای جلوگیری از یک آسیب‌پذیری امنیتی احتمالی ([mutation XSS](https://www.securitum.com/mutation-xss-via-mathml-mutation-dompurify-2-0-17-bypass.html)) انجام می‌شود که در آن مهاجم می‌تواند ورودی‌ای بسازد که از یک [تابع پاک‌سازی](/en-US/docs/Web/Security/Attacks/XSS#sanitization) عبور کند و در نتیجه حملهٔ اسکریپت‌نویسی بین‌سایتی (XSS) ممکن شود.

### ملاحظات Shadow DOM

سریال‌سازی درخت DOM که از این ویژگی خوانده می‌شود شامل {{glossary("shadow tree", "shadow root")}} نیست.
اگر می‌خواهید یک سریال‌سازی HTML از عنصری بگیرید که shadow rootها را هم شامل شود، باید به‌جای آن از متد {{domxref("Element.getHTML()")}} استفاده کنید.
توجه داشته باشید که این متد _محتوای_ عنصر را دریافت می‌کند.

به‌طور مشابه، هنگام تنظیم محتوای عنصر با استفاده از `outerHTML`، ورودی HTML به عناصر DOMی تجزیه می‌شود که شامل shadow root نیستند.
بنابراین برای مثال [`<template>`](/en-US/docs/Web/HTML/Reference/Elements/template) صرف‌نظر از اینکه ویژگی [`shadowrootmode`](/en-US/docs/Web/HTML/Reference/Elements/template#shadowrootmode) مشخص شده باشد یا نه، به صورت {{domxref("HTMLTemplateElement")}} تجزیه می‌شود.
اگر می‌خواهید _محتوای_ یک عنصر را از ورودی HTML که شامل shadow rootهای اعلانی (declarative) است تنظیم کنید، باید به‌جای آن از {{domxref("Element.setHTMLUnsafe()")}} یا {{domxref("ShadowRoot.setHTMLUnsafe()")}} استفاده کنید.

### ملاحظات امنیتی

ویژگی `outerHTML` بردار احتمالی برای حملات [اسکریپت‌نویسی بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) است، زیرا می‌توان از آن برای تزریق رشته‌های بالقوه ناامن ارائه‌شده توسط کاربر به DOM استفاده کرد.
اگرچه این ویژگی از اجرا شدن عناصر {{HTMLElement("script")}} هنگام تزریق جلوگیری می‌کند، اما در برابر بسیاری از روش‌های دیگری که مهاجمان می‌توانند HTML را برای اجرای جاوااسکریپت مخرب بسازند، آسیب‌پذیر است.
برای مثال، مثال زیر کد موجود در رویداد `error` را اجرا می‌کند، زیرا مقدار `src` در {{htmlelement("img")}} یک URL تصویر معتبر نیست:

```js
const name = "<img src='x' onerror='alert(1)'>";
element.outerHTML = name; // هشدار را نشان می‌دهد
```

می‌توانید این مسائل را با اختصاص دادن همیشگی اشیاء {{domxref("TrustedHTML")}} به‌جای رشته‌ها و [اجباری کردن trusted types](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) با استفاده از دستور CSP [`require-trusted-types-for`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/require-trusted-types-for) کاهش دهید.
این کار تضمین می‌کند که ورودی از یک تابع تبدیل عبور کند، که این فرصت را دارد تا ورودی را قبل از تزریق [پاک‌سازی](/en-US/docs/Web/Security/Attacks/XSS#sanitization) کند و مارک‌آپ بالقوه خطرناک را حذف نماید.

## مثال‌ها

### دریافت سریال‌سازی یک عنصر

خواندن `outerHTML` باعث می‌شود عامل کاربر (user agent) عنصر را سریال‌سازی کند.

با توجه به HTML زیر:

```html
<div id="example">
  <p>Content</p>
  <p>Further Elaborated</p>
</div>
```

می‌توانید مارک‌آپ مربوط به {{htmlelement("div")}} را به صورت زیر دریافت و ثبت (log) کنید:

```js
const myElement = document.querySelector("#example");
const contents = myElement.outerHTML;
console.log(contents);
// '<div id="example">\n  <p>Content</p>\n  <p>Further Elaborated</p>\n</div>'
```

### جایگزینی عنصر

در این مثال، عنصری را در DOM با اختصاص HTML به ویژگی `outerHTML` آن جایگزین می‌کنیم.
برای کاهش ریسک XSS، ابتدا یک شیء `TrustedHTML` از رشته‌ای که HTML را شامل می‌شود می‌سازیم و سپس آن شیء را به `outerHTML` اختصاص می‌دهیم.

Trusted types هنوز در همه مرورگرها پشتیبانی نمی‌شود، بنابراین ابتدا [tinyfill مربوط به trusted types](/en-US/docs/Web/API/Trusted_Types_API#trusted_types_tinyfill) را تعریف می‌کنیم.
این قطعه به‌عنوان جایگزینی شفاف برای API جاوااسکریپت Trusted Types عمل می‌کند:

```js
if (typeof trustedTypes === "undefined")
  trustedTypes = { createPolicy: (n, rules) => rules };
```

سپس یک {{domxref("TrustedTypePolicy")}} تعریف می‌کنیم که یک {{domxref("TrustedTypePolicy/createHTML", "createHTML()")}} برای تبدیل رشتهٔ ورودی به نمونه‌های {{domxref("TrustedHTML")}} تعریف می‌کند.
معمولاً پیاده‌سازی‌های `createHTML()` از کتابخانه‌ای مانند [DOMPurify](https://github.com/cure53/DOMPurify) برای پاک‌سازی ورودی استفاده می‌کنند، همان‌طور که در زیر نشان داده شده است:

```js
const policy = trustedTypes.createPolicy("my-policy", {
  createHTML: (input) => DOMPurify.sanitize(input),
});
```

سپس از این شیء `policy` برای ایجاد یک شیء `TrustedHTML` از رشتهٔ ورودی بالقوه ناامن استفاده می‌کنیم و نتیجه را به عنصر اختصاص می‌دهیم:

```js
// رشتهٔ بالقوه مخرب
const untrustedString = "<p>I might be XSS</p><img src='x' onerror='alert(1)'>";

// ایجاد یک نمونه TrustedHTML با استفاده از policy
const trustedHTML = policy.createHTML(untrustedString);

// تزریق TrustedHTML (که شامل یک رشتهٔ قابل اعتماد است)
const element = document.querySelector("#container");
element.outerHTML = trustedHTML; // عنصر با شناسه "container" جایگزین می‌شود

// توجه کنید که div با شناسه #container دیگر بخشی از درخت سند نیست
```

> [!WARNING]
> اگرچه می‌توانید مستقیماً یک رشته را به `outerHTML` اختصاص دهید، این کار یک [ریسک امنیتی](#security_considerations) است اگر رشته‌ای که قرار است درج شود شامل محتوای بالقوه مخرب باشد.
> باید از `TrustedHTML` استفاده کنید تا مطمئن شوید محتوا قبل از درج پاک‌سازی شده است، و باید یک هدر CSP برای [اجباری کردن trusted types](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) تنظیم کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- سریال‌سازی درختان DOM به رشته‌های XML: {{domxref("XMLSerializer")}}
- تجزیه XML یا HTML به درختان DOM: {{domxref("DOMParser")}}
- {{domxref("HTMLElement.outerText")}}