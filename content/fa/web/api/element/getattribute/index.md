---
title: "Element: getAttribute() method"
short-title: getAttribute()
slug: Web/API/Element/getAttribute
page-type: web-api-instance-method
browser-compat: api.Element.getAttribute
---

{{APIRef("DOM")}}

متد **`getAttribute()`** در رابط {{domxref("Element")}} مقدار یک ویژگی مشخص را روی عنصر برمی‌گرداند.

اگر ویژگی موردنظر وجود نداشته باشد، مقدار بازگشتی `null` خواهد بود.

اگر نیاز به بررسی ویژگی‌های گره {{domxref("Attr")}} دارید، می‌توانید به جای آن از متد {{domxref("Element.getAttributeNode()", "getAttributeNode()")}} استفاده کنید.

## نحو (Syntax)

```js-nolint
getAttribute(attributeName)
```

### پارامترها

- `attributeName`
  - : نام ویژگی‌ای که می‌خواهید مقدار آن را دریافت کنید.

### مقدار بازگشتی

اگر ویژگی وجود داشته باشد، رشته‌ای حاوی مقدار `attributeName` است؛ در غیر این صورت `null` برمی‌گردد.

## مثال‌ها

```html
<!-- example div in an HTML DOC -->
<div id="div1">Hi Champ!</div>
```

```js
const div1 = document.getElementById("div1");
// <div id="div1">Hi Champ!</div>

const exampleAttr = div1.getAttribute("id");
// "div1"

const lang = div1.getAttribute("lang");
// null
```

## توضیحات

### تبدیل به حروف کوچک

وقتی `getAttribute()` روی یک عنصر HTML در DOM که به‌عنوان سند HTML علامت‌گذاری شده فراخوانی شود، قبل از ادامه، آرگومان خود را به حروف کوچک تبدیل می‌کند.

### رمزگشایی مراجع کاراکتری در مقادیر ویژگی

[مراجع کاراکتری](/en-US/docs/Glossary/Character_reference) HTML موجود در نشانه‌گذاری منبع یک ویژگی (مانند `&lt;`، `&amp;` یا `&#x3C;`) هنگام تجزیه سند توسط تجزیه‌گر HTML رمزگشایی می‌شوند؛ بنابراین `getAttribute()` مقدار رمزگشایی‌شده را برمی‌گرداند، نه کد منبع اصلی را.

با فرض کد زیر:

```html
<div id="example" data-payload="&lt;b&gt;hi&lt;/b&gt;"></div>
```

فراخوانی `document.getElementById("example").getAttribute("data-payload")` رشته `"<b>hi</b>"` را برمی‌گرداند.

در نظر گرفتن مقدار بازگشتی `getAttribute()` به‌عنوان HTML از پیش فرار داده‌شده ناامن است. اگر ویژگی‌ای را بخوانید که داده‌ای غیرقابل‌اعتماد دارد و سپس آن را به {{domxref("Element.innerHTML", "innerHTML")}} اختصاص دهید یا به‌عنوان نشانه‌گذاری در سند درج کنید، هر مرجع HTML که برای فرار دادن کاراکترهای خاص استفاده شده بود قبلاً رمزگشایی شده است و نتیجه می‌تواند برای [حمله اسکریپت بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) مورد سوءاستفاده قرار گیرد.

برای داده‌های غیرقابل‌اعتماد به‌جای `innerHTML` از {{domxref("Node.textContent", "textContent")}} (یا هر API امن متنی دیگر) استفاده کنید.

### دریافت مقادیر nonce

به دلایل امنیتی، nonceهای [CSP](/en-US/docs/Web/HTTP/Guides/CSP) از منابع غیر اسکریپتی مانند انتخابگرهای CSS و همچنین فراخوانی‌های `.getAttribute("nonce")` پنهان می‌شوند.

```js example-bad
let nonce = script.getAttribute("nonce");
// returns empty string
```

به‌جای دریافت nonce از ویژگی محتوایی، از ویژگی {{domxref("HTMLElement/nonce", "nonce")}} استفاده کنید:

```js
let nonce = script.nonce;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.hasAttribute()")}}
- {{domxref("Element.setAttribute()")}}
- {{domxref("Element.removeAttribute()")}}
- {{domxref("Element.toggleAttribute()")}}