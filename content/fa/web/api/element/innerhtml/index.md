---
title: "Element: innerHTML property"
---

---
title: "Element: innerHTML property"
short-title: innerHTML
slug: Web/API/Element/innerHTML
page-type: web-api-instance-property
browser-compat: api.Element.innerHTML
---

{{APIRef("DOM")}}

> [!WARNING]
> این ویژگی ورودی خود را به عنوان HTML تجزیه می‌کند و نتیجه را در DOM می‌نویسد.
> APIهایی از این دست به عنوان [نقاط تزریق (injection sinks)](/en-US/docs/Web/API/Trusted_Types_API#concepts_and_usage) شناخته می‌شوند و اگر ورودی در اصل از سوی مهاجمی آمده باشد، به‌طور بالقوه برداری (vector) برای حملات [اسکریپت بین سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) هستند.
>
> می‌توانید این ریسک را با همواره اختصاص دادنِ اشیاء `TrustedHTML` به‌جای رشته‌ها و [الزامی کردن trusted types](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) کاهش دهید.
> برای اطلاعات بیشتر به [ملاحظات امنیتی](#security_considerations) مراجعه کنید.

ویژگی **`innerHTML`** در رابط {{domxref("Element")}}، نشانه‌گذاری HTML یا XML موجود درون عنصر را دریافت یا تنظیم می‌کند و در هر دو حالت، تمامی {{glossary("shadow tree", "shadow roots")}} را نادیده می‌گیرد.

برای درج HTML در سند به‌جای جایگزین کردن محتوای یک عنصر، از متد {{domxref("Element.insertAdjacentHTML", "insertAdjacentHTML()")}} استفاده کنید.

## مقدار

خواندن این ویژگی، رشته‌ای برمی‌گرداند که شامل سریال‌سازی HTML از فرزندان عنصر است.

تنظیم این ویژگی یا یک شیء {{domxref("TrustedHTML")}} را می‌پذیرد یا یک رشته را. این ویژگی، مقدار را به عنوان HTML تجزیه می‌کند و همهٔ فرزندان عنصر را با نتیجهٔ آن جایگزین می‌کند.
وقتی روی مقدار `null` تنظیم شود، آن مقدار `null` به رشتهٔ خالی (`""`) تبدیل می‌شود؛ بنابراین `elt.innerHTML = null` معادل `elt.innerHTML = ""` است.

### استثناها

- `SyntaxError` {{domxref("DOMException")}}
  - : اگر تلاش شود مقدار `innerHTML` با رشته‌ای تنظیم شود که HTML خوش‌فرم نیست، این خطا پرتاب می‌شود.
- `TypeError`
  - : اگر ویژگی با یک رشته تنظیم شود، در حالی که [Trusted Types](/en-US/docs/Web/API/Trusted_Types_API) توسط [CSP الزامی شده](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) باشند و هیچ خط‌مشی پیش‌فرضی تعریف نشده باشد، این خطا پرتاب می‌شود.
- `NoModificationAllowedError` {{domxref("DOMException")}}
  - : اگر تلاش شود HTML در گره‌ای درج شود که والد آن یک {{domxref("Document")}} است، این خطا پرتاب می‌شود.

## توضیحات

`innerHTML` یک سریال‌سازی از عناصر DOM فرزندِ تو در توی درون عنصر دریافت می‌کند، یا HTML یا XMLایی را تنظیم می‌کند که باید تجزیه شود تا درخت DOM درون عنصر را جایگزین کند.

توجه داشته باشید که برخی مرورگرها کاراکترهای `<` و `>` را وقتی در مقادیر ویژگی‌ها ظاهر می‌شوند، به صورت `&lt;` و `&gt;` سریال‌سازی می‌کنند (به [سازگاری مرورگر](#browser_compatibility) مراجعه کنید).
این کار برای جلوگیری از یک آسیب‌پذیری امنیتی بالقوه ([XSS جهشی](https://www.securitum.com/mutation-xss-via-mathml-mutation-dompurify-2-0-17-bypass.html)) انجام می‌شود؛ در این نوع حمله، مهاجم می‌تواند ورودی‌ای بسازد که از [تابع پاک‌سازی](/en-US/docs/Web/Security/Attacks/XSS#sanitization) عبور کند و حملهٔ اسکریپت بین سایتی (XSS) را ممکن سازد.

### ملاحظات Shadow DOM

سریال‌سازی درخت DOM که از این ویژگی خوانده می‌شود، شامل {{glossary("shadow tree", "shadow roots")}} نیست — اگر می‌خواهید رشتهٔ HTMLایی به دست آورید که شامل ریشه‌های سایه است، باید به‌جای آن از متدهای {{domxref("Element.getHTML()")}} یا {{domxref("ShadowRoot.getHTML()")}} استفاده کنید.

به‌طور مشابه، وقتی محتوای عنصر با استفاده از `innerHTML` تنظیم می‌شود، رشتهٔ HTML به عناصر DOMایی تجزیه می‌شود که ریشه‌های سایه ندارند.
بنابراین برای مثال، [`<template>`](/en-US/docs/Web/HTML/Reference/Elements/template) صرف‌نظر از اینکه ویژگی [`shadowrootmode`](/en-US/docs/Web/HTML/Reference/Elements/template#shadowrootmode) مشخص شده باشد یا نه، به عنصر {{domxref("HTMLTemplateElement")}} تجزیه می‌شود.
برای تنظیم محتوای یک عنصر از روی رشتهٔ HTMLایی که شامل ریشه‌های سایهٔ اعلانی (declarative shadow roots) است، باید به‌جای آن از {{domxref("Element.setHTMLUnsafe()")}} یا {{domxref("ShadowRoot.setHTMLUnsafe()")}} استفاده کنید.

### ملاحظات امنیتی

ویژگی `innerHTML` احتمالاً رایج‌ترین بردار (vector) برای حملات [اسکریپت بین سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) است؛ جایی که رشته‌های بالقوهٔ ناامنِ ارائه‌شده توسط کاربر، بدون اینکه ابتدا پاک‌سازی شوند، به DOM تزریق می‌شوند.
اگرچه این ویژگی از اجرای عناصر {{HTMLElement("script")}} هنگام تزریق جلوگیری می‌کند، اما نسبت به بسیاری از روش‌های دیگری که مهاجمان می‌توانند با آن‌ها HTML را برای اجرای جاوااسکریپت مخرب بسازند، آسیب‌پذیر است.
برای مثال، مثال زیر کد موجود در کنترل‌کنندهٔ رویداد `error` را اجرا می‌کند، زیرا مقدار `src` عنصر {{htmlelement("img")}} یک URL تصویر معتبر نیست:

```js
const name = "<img src='x' onerror='alert(1)'>";
el.innerHTML = name; // shows the alert
```

می‌توانید این مشکلات را با همواره اختصاص دادن اشیاء {{domxref("TrustedHTML")}} به‌جای رشته‌ها و [الزامی کردن trusted types](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) با استفاده از دستور CSP [`require-trusted-types-for`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/require-trusted-types-for) کاهش دهید.
این کار تضمین می‌کند که ورودی از یک تابع تبدیل عبور کند؛ تابعی که فرصت [پاک‌سازی](/en-US/docs/Web/Security/Attacks/XSS#sanitization) ورودی را دارد تا نشانه‌گذاری بالقوهٔ خطرناک را پیش از تزریق حذف کند.

> [!NOTE]
> وقتی می‌دانید محتوای ارائه‌شده توسط کاربر باید متن ساده (plain text) باشد، باید از {{domxref("Node.textContent")}} استفاده کنید.
> این کار از تجزیه‌شدن آن به عنوان HTML جلوگیری می‌کند.

## مثال‌ها

### خواندن محتوای HTML یک عنصر

خواندن `innerHTML` باعث می‌شود عامل کاربر (user agent) فرزندان عنصر را سریال‌سازی کند.

با توجه به HTML زیر:

```html
<div id="example">
  <p>My name is Joe</p>
</div>
```

می‌توانید نشانه‌گذاری مربوط به محتوای {{htmlelement("div")}} بیرونی را به صورت زیر دریافت و ثبت (log) کنید:

```js
const myElement = document.querySelector("#example");
const contents = myElement.innerHTML;
console.log(contents); // "\n  <p>My name is Joe</p>\n"
```

### جایگزین کردن محتوای یک عنصر

در این مثال، DOM یک عنصر را با اختصاص دادن HTML به ویژگی `innerHTML` آن عنصر جایگزین می‌کنیم.
برای کاهش ریسک XSS، ابتدا از رشته‌ای که HTML را شامل می‌شود یک شیء `TrustedHTML` می‌سازیم و سپس آن شیء را به `innerHTML` اختصاص می‌دهیم.

Trusted types هنوز در همهٔ مرورگرها پشتیبانی نمی‌شوند، بنابراین ابتدا [tinyfill مربوط به trusted types](/en-US/docs/Web/API/Trusted_Types_API#trusted_types_tinyfill) را تعریف می‌کنیم.
این قطعه به عنوان جایگزینی شفاف برای API جاوااسکریپت Trusted Types عمل می‌کند:

```js
if (typeof trustedTypes === "undefined")
  trustedTypes = { createPolicy: (n, rules) => rules };
```

سپس یک {{domxref("TrustedTypePolicy")}} می‌سازیم که یک متد {{domxref("TrustedTypePolicy/createHTML", "createHTML()")}} برای تبدیل رشتهٔ ورودی به نمونه‌های {{domxref("TrustedHTML")}} تعریف می‌کند.
معمولاً پیاده‌سازی‌های `createHTML()` از کتابخانه‌ای مانند [DOMPurify](https://github.com/cure53/DOMPurify) برای پاک‌سازی ورودی استفاده می‌کنند، همان‌طور که در زیر نشان داده شده است:

```js
const policy = trustedTypes.createPolicy("my-policy", {
  createHTML: (input) => DOMPurify.sanitize(input),
});
```

سپس از این شیءِ `policy` برای ساختن یک شیء `TrustedHTML` از رشتهٔ ورودی بالقوهٔ ناامن استفاده می‌کنیم و نتیجه را به عنصر اختصاص می‌دهیم:

```js
// The potentially malicious string
const untrustedString = "<p>I might be XSS</p><img src='x' onerror='alert(1)'>";

// Create a TrustedHTML instance using the policy
const trustedHTML = policy.createHTML(untrustedString);

// Inject the TrustedHTML (which contains a trusted string)
const element = document.querySelector("#container");
element.innerHTML = trustedHTML;
```

> [!WARNING]
> اگرچه می‌توانید یک رشته را مستقیماً به `innerHTML` اختصاص دهید، اما اگر رشته‌ای که قرار است درج شود حاوی محتوای بالقوهٔ مخرب باشد، این کار یک [ریسک امنیتی](#security_considerations) است.
> باید از `TrustedHTML` استفاده کنید تا مطمئن شوید محتوا قبل از درج پاک‌سازی می‌شود، و همچنین باید یک هدر CSP برای [الزامی کردن trusted types](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) تنظیم کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("Node.textContent")}} و {{domxref("HTMLElement.innerText")}}
- {{domxref("Element.insertAdjacentHTML()")}}
- {{domxref("Element.outerHTML")}}
- تجزیه HTML یا XML به یک درخت DOM: {{domxref("DOMParser")}}
- سریال‌سازی یک درخت DOM به رشتهٔ XML: {{domxref("XMLSerializer")}}
- {{domxref("Element.getHTML()")}}
- {{domxref("ShadowRoot.getHTML()")}}
- {{domxref("Element.setHTMLUnsafe()")}}
- {{domxref("ShadowRoot.setHTMLUnsafe()")}}
- [Trusted Types API](/en-US/docs/Web/API/Trusted_Types_API)