---
title: "HTMLScriptElement: supports() static method"
short-title: supports()
slug: Web/API/HTMLScriptElement/supports_static
page-type: web-api-static-method
browser-compat: api.HTMLScriptElement.supports_static
---

{{APIRef("HTML DOM")}}

متد ایستا (static) **`supports()`** در رابط {{domxref("HTMLScriptElement")}} یک روش ساده و یکپارچه برای تشخیص ویژگی (feature-detection) نوع اسکریپت‌هایی که توسط عامل کاربر (user agent) پشتیبانی می‌شوند، ارائه می‌دهد.

انتظار می‌رود این متد برای اسکریپت‌های کلاسیک (classic) و ماژول (module) که توسط بیشتر مرورگرهای مدرن پشتیبانی می‌شوند، مقدار `true` را بازگرداند.

## نحو (Syntax)

```js-nolint
HTMLScriptElement.supports(type)
```

### پارامترها

- `type`
  - : یک رشته (string literal) که نوع اسکریپتی را که باید پشتیبانی آن بررسی شود، مشخص می‌کند.
    مقادیر پشتیبانی‌شده به حروف بزرگ و کوچک حساس هستند (case sensitive) و شامل موارد زیر می‌باشند:
    - `"classic"`
      - : بررسی می‌کند که آیا _اسکریپت‌های کلاسیک_ پشتیبانی می‌شوند.
        اسکریپت‌های «کلاسیک» همان فایل‌های جاوااسکریپت معمولی/سنتی هستند که پیش از اسکریپت‌های ماژول وجود داشتند.
    - `"module"`
      - : بررسی می‌کند که آیا [اسکریپت‌های ماژول](/en-US/docs/Web/JavaScript/Guide/Modules) پشتیبانی می‌شوند.
    - `"importmap"`
      - : بررسی می‌کند که آیا [نقشه‌های واردات (import maps)](/en-US/docs/Web/HTML/Reference/Elements/script/type/importmap) پشتیبانی می‌شوند.
    - `"speculationrules"`
      - : بررسی می‌کند که آیا [قوانین حدس (speculation rules)](/en-US/docs/Web/API/Speculation_Rules_API) پشتیبانی و فعال هستند.

    هر مقدار دیگری باعث می‌شود متد `false` را بازگرداند.

### مقدار بازگشتی

در صورت پشتیبانی از نوع اسکریپت مشخص‌شده، مقدار `true` و در غیر این صورت `false` را بازمی‌گرداند.

## مثال‌ها

کد زیر نشان می‌دهد که چگونه می‌توان بررسی کرد که آیا `HTMLScriptElement.supports()` تعریف شده است و در صورت تعریف، از آن برای تست پشتیبانی از انواع خاص اسکریپت‌ها استفاده کرد.

```js
const log = document.getElementById("log");

function checkSupport(type) {
  const result = HTMLScriptElement.supports(type) ? "true" : "false";
  log.textContent += `HTMLScriptElement.supports('${type}') is ${result}\n`;
}

if (typeof HTMLScriptElement.supports === "undefined") {
  log.textContent = "HTMLScriptElement.supports() method is not supported";
} else {
  // Check if various script types are supported
  checkSupport("module");
  checkSupport("classic");
  checkSupport("importmap");
  checkSupport("speculationrules");
  // Any other value will cause the method to return false
  checkSupport("anything else");
}
```

```html hidden
<textarea id="log" rows="6" cols="80"></textarea>
```

{{ EmbedLiveSample('Examples') }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLScriptElement")}}
- {{HTMLElement("script")}}
- [ماژول‌های جاوااسکریپت](/en-US/docs/Web/JavaScript/Guide/Modules)
- سازنده {{domxref("Worker/Worker","Worker")}}