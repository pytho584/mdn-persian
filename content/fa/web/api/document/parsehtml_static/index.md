---
title: "Document: parseHTML() static method"
short-title: parseHTML()
slug: Web/API/Document/parseHTML_static
page-type: web-api-static-method
browser-compat: api.Document.parseHTML_static
---

{{APIRef("DOM")}}

متد ایستای **`parseHTML()`** در شیء {{domxref("Document")}} روشی ایمن در برابر حملات XSS برای تجزیه و پاکسازی یک رشته HTML به منظور ایجاد یک نمونه جدید {{domxref("Document")}} فراهم می‌کند.

## Syntax

```js-nolint
Document.parseHTML(input)
Document.parseHTML(input, options)
```

### Parameters

- `input`
  - : یک رشته HTML که باید پاکسازی شده و به ریشه سایه (shadow root) تزریق شود.
- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها با پارامترهای اختیاری زیر:
    - `sanitizer`
      - : یک شیء {{domxref("Sanitizer")}} یا {{domxref("SanitizerConfig")}} که تعیین می‌کند چه عناصری از ورودی مجاز یا حذف شوند، یا رشته `"default"` برای [پیکربندی پیش‌فرض پاک‌ساز](/en-US/docs/Web/API/HTML_Sanitizer_API/Default_sanitizer_configuration). این متد هر عنصر و ویژگی ناایمن در برابر XSS را حتی اگر توسط پاک‌ساز مجاز شده باشد، حذف می‌کند. اگر مشخص نشود، از پیکربندی پیش‌فرض `Sanitizer` استفاده می‌شود.

        توجه داشته باشید که اگر از یک پیکربندی یکسان چندین بار استفاده می‌کنید، انتظار می‌رود استفاده از یک `Sanitizer` و تغییر آن در زمان نیاز کارآمدتر باشد.

### Return value

یک {{domxref("Document")}}.

### Exceptions

- `TypeError`
  - : این خطا پرتاب می‌شود اگر `options.sanitizer` یکی از موارد زیر را دریافت کند:
    - یک {{domxref("SanitizerConfig")}} که [معتبر](/en-US/docs/Web/API/SanitizerConfig#valid_configuration) نیست. به عنوان مثال، پیکربندی که شامل هر دو تنظیمات «مجاز» و «حذف شده» باشد.
    - رشته‌ای که مقدار `"default"` را نداشته باشد.
    - مقداری که {{domxref("Sanitizer")}}، {{domxref("SanitizerConfig")}} یا رشته نباشد.

## Description

متد **`parseHTML()`** یک رشته HTML را تجزیه و پاکسازی می‌کند تا یک نمونه جدید {{domxref("Document")}} ایجاد کند که در برابر XSS ایمن باشد. `Document` حاصل دارای [نوع محتوا](/en-US/docs/Web/API/Document/contentType) "text/html"، [مجموعه کاراکتر](/en-US/docs/Web/API/Document/characterSet) UTF-8 و URL "about:blank" خواهد بود.

اگر هیچ پاک‌سازی در پارامتر `options.sanitizer` مشخص نشود، `parseHTML()` با [پیکربندی پیش‌فرض پاک‌ساز](/en-US/docs/Web/API/HTML_Sanitizer_API/Default_sanitizer_configuration) استفاده می‌شود. این پیکربندی برای اکثر موارد استفاده مناسب است زیرا از حملات XSS و همچنین حملات دیگری مانند کلیک‌ربایی (clickjacking) یا جعل (spoofing) جلوگیری می‌کند.

یک `Sanitizer` یا `SanitizerConfig` سفارشی می‌تواند مشخص شود تا انتخاب کند کدام عناصر، ویژگی‌ها و نظرات مجاز یا حذف شوند. توجه داشته باشید که حتی اگر گزینه‌های ناایمن توسط پاک‌ساز مجاز شوند، باز هم در هنگام استفاده از این متد حذف خواهند شد (همان عناصری را حذف می‌کند که یک پاک‌ساز که {{domxref('Sanitizer.removeUnsafe()')}} روی آن فراخوانی شده است، حذف می‌کند).

HTML ورودی ممکن است شامل [ریشه‌های سایه اعلانی (declarative shadow roots)](/en-US/docs/Web/HTML/Reference/Elements/template#declarative_shadow_dom) باشد. اگر رشته HTML بیش از یک [ریشه سایه اعلانی](/en-US/docs/Web/HTML/Reference/Elements/template#declarative_shadow_dom) را در یک میزبان سایه خاص تعریف کند، تنها اولین {{domxref("ShadowRoot")}} ایجاد می‌شود — اعلان‌های بعدی به عنوان عناصر {{htmlelement("template")}} درون آن ریشه سایه تجزیه می‌شوند.

`parseHTML()` باید به جای {{domxref("Document.parseHTMLUnsafe_static", "Document.parseHTMLUnsafe()")}} استفاده شود، مگر اینکه نیاز خاصی به مجاز کردن عناصر و ویژگی‌های ناایمن وجود داشته باشد. اگر HTML مورد تجزیه نیازی به شامل موجودیت‌های HTML ناایمن ندارد، باید از `Document.parseHTML()` استفاده کنید.

توجه داشته باشید که از آنجایی که این متد همواره رشته‌های ورودی را از موجودیت‌های ناایمن در برابر XSS پاکسازی می‌کند، با استفاده از [API انواع امن (Trusted Types API)](/en-US/docs/Web/API/Trusted_Types_API) ایمن یا تأیید نمی‌شود.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Document.parseHTMLUnsafe_static", "Document.parseHTMLUnsafe()")}}
- {{domxref("Element.setHTML()")}} و {{domxref("Element.setHTMLUnsafe()")}}
- {{domxref("ShadowRoot.setHTML()")}} و {{domxref("ShadowRoot.setHTMLUnsafe()")}}
- {{domxref("DOMParser.parseFromString()")}} برای تجزیه HTML یا XML به یک درخت DOM
- [HTML Sanitizer API](/en-US/docs/Web/API/HTML_Sanitizer_API)