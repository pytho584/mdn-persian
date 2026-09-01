---
title: "Element: getHTML() method"
short-title: getHTML()
slug: Web/API/Element/getHTML
page-type: web-api-instance-method
browser-compat: api.Element.getHTML
---

{{APIRef("DOM")}}

متد **`getHTML()`** از رابط {{domxref("Element")}} برای سریال‌سازی (تبدیل به رشته) DOM یک عنصر به یک رشته HTML استفاده می‌شود.

این متد یک آرگومان `options` ارائه می‌دهد که امکان سریال‌سازی گره‌های فرزندی را که ریشه‌های سایه (shadow roots) هستند فراهم می‌کند. گزینه‌ها می‌توانند برای شامل شدن ریشه‌های سایه تو در تو که به عنوان {{domxref("ShadowRoot/serializable","serializable")}} (قابل سریال‌سازی) تنظیم شده‌اند، و/یا یک آرایه مشخص از اشیاء {{domxref("ShadowRoot")}} (که می‌توانند باز یا بسته باشند) استفاده شوند.

بدون آرگومان، گره‌های فرزندی که ریشه‌های سایه هستند سریال‌سازی نمی‌شوند و این متد دقیقاً مانند خواندن مقدار {{domxref("Element.innerHTML")}} عمل می‌کند.

توجه داشته باشید که برخی مرورگرها کاراکترهای `<` و `>` را به صورت `&lt;` و `&gt;` در مواقعی که در مقادیر ویژگی‌ها ظاهر می‌شوند، سریال‌سازی می‌کنند (به [سازگاری مرورگر](#browser_compatibility) مراجعه کنید). این کار برای جلوگیری از یک آسیب‌پذیری امنیتی بالقوه ([mutation XSS](https://www.securitum.com/mutation-xss-via-mathml-mutation-dompurify-2-0-17-bypass.html)) است که در آن یک مهاجم می‌تواند ورودی‌ای را طراحی کند که از [تابع پالایش](/en-US/docs/Web/Security/Attacks/XSS#sanitization) عبور کرده و یک حمله اسکریپت‌نویسی بین‌سایتی (XSS) را ممکن سازد.

## نحوه استفاده

```js-nolint
getHTML(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء options با پارامترهای اختیاری زیر:
    - `serializableShadowRoots`
      - : یک مقدار بولی که مشخص می‌کند آیا ریشه‌های سایه {{domxref("ShadowRoot/serializable","serializable")}} (قابل سریال‌سازی) شامل شوند یا خیر. مقدار پیش‌فرض `false` است.
    - `shadowRoots`
      - : یک آرایه از اشیاء {{domxref("ShadowRoot")}} برای سریال‌سازی. این اشیاء صرف‌نظر از اینکه به عنوان `serializable` علامت‌گذاری شده‌اند یا خیر، یا باز یا بسته هستند، شامل می‌شوند. مقدار پیش‌فرض یک آرایه خالی است.

### مقدار بازگشتی

یک رشته که نمایانگر سریال‌سازی HTML عنصر است.

### استثناها

هیچ‌کدام.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ShadowRoot.getHTML()")}}
- {{domxref("Element.innerHTML")}}
- {{domxref("Element.setHTMLUnsafe()")}}
- {{domxref("ShadowRoot.setHTMLUnsafe()")}}