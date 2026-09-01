---
title: "Document: write() method"
short-title: write()
slug: Web/API/Document/write
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.Document.write
---

{{ApiRef("DOM")}}{{deprecated_header}}

> [!WARNING]
> استفاده از متد `document.write()` به‌شدت توصیه نمی‌شود.
> از به‌کارگیری آن خودداری کنید و در صورت امکان، در کدهای موجود آن را جایگزین کنید.
>
> همانطور که [خود مشخصات HTML هشدار می‌دهد](<https://html.spec.whatwg.org/multipage/dynamic-markup-insertion.html#document.write()>):
>
> > این متد رفتار بسیار خاص و غیرعادی دارد.
> > در برخی موارد، این متد می‌تواند بر وضعیت [تجزیه‌گر HTML](https://html.spec.whatwg.org/multipage/parsing.html#html-parser) در حالی که تجزیه‌گر در حال اجراست تأثیر بگذارد و در نتیجه DOMی ایجاد شود که با منبع سند مطابقت ندارد (مثلاً اگر رشته نوشته‌شده رشته «`<plaintext>`» یا «`<!--`» باشد).
> > در موارد دیگر، این فراخوانی می‌تواند ابتدا صفحه فعلی را پاک کند، همان‌طور که گویی {{domxref("document.open()")}} فراخوانی شده باشد.
> > در مواردی دیگر، این متد به سادگی نادیده گرفته می‌شود یا استثنا پرتاب می‌کند. به عوامل کاربر به‌صراحت [اجازه داده شده است که از اجرای عناصر `script` درج‌شده از طریق این متد خودداری کنند](https://html.spec.whatwg.org/multipage/parsing.html#document-written-scripts-intervention).
> > و برای بدتر کردن اوضاع، رفتار دقیق این متد در برخی موارد می‌تواند به تأخیر شبکه بستگی داشته باشد که می‌تواند به خطاهایی منجر شود که اشکال‌زدایی آن‌ها بسیار دشوار است.
> > به تمام این دلایل، استفاده از این متد به‌شدت توصیه نمی‌شود.

> [!WARNING]
> این متد ورودی خود را به‌عنوان HTML تجزیه می‌کند و نتیجه را در DOM می‌نویسد.
> APIهایی مانند این به‌عنوان [سینک‌های تزریق](/en-US/docs/Web/API/Trusted_Types_API#concepts_and_usage) شناخته می‌شوند و اگر ورودی در ابتدا از طرف مهاجم باشد، به‌طور بالقوه بردار حمله‌ای برای [اسکریپت‌نویسی بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) هستند.
>
> می‌توانید این خطر را با همیشه ارسال اشیاء `TrustedHTML` به‌جای رشته‌ها و [اجباری کردن انواع مورد اعتماد](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) کاهش دهید.
> برای اطلاعات بیشتر، [ملاحظات امنیتی](#security_considerations) را ببینید.

متد **`write()`** از رابط {{domxref("Document")}} متن را در یک یا چند پارامتر {{domxref("TrustedHTML")}} یا رشته به جریان سندی می‌نویسد که توسط {{domxref("document.open()")}} باز شده است.

## نحو (Syntax)

```js-nolint
write(markup)
write(markup, markup2)
write(markup, markup2, /* …, */ markupN)
```

### پارامترها

- `markup`, …, `markupN`
  - : اشیاء {{domxref("TrustedHTML")}} یا رشته‌های حاوی نشانه‌گذاری (markup) که باید در سند نوشته شوند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : متد روی یک سند XML فراخوانی شده باشد، یا در حالی فراخوانی شود که تجزیه‌گر در حال اجرای سازنده یک عنصر سفارشی (custom element) است.
- `TypeError`
  - : یک رشته به‌عنوان یکی از پارامترها زمانی ارسال شود که [انواع مورد اعتماد اجباری هستند](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) و [هیچ خط‌مشی پیش‌فرضی برای ایجاد اشیاء {{domxref("TrustedHTML")}} تعریف نشده است](/en-US/docs/Web/API/TrustedTypePolicyFactory/createPolicy#creating_a_default_policy).

## توضیحات

`document.write()` متن نشانه‌گذاری موجود در اشیاء ارسال‌شده به‌عنوان پارامتر را به مدل شیء سند (DOM) سند باز، به ترتیبی که پارامترها مشخص شده‌اند، تجزیه می‌کند.

از آنجا که `document.write()` به **جریان** سند می‌نویسد، فراخوانی `document.write()` روی یک سند بسته (بارگذاری‌شده) (بدون فراخوانی قبلی {{domxref("document.open()")}}) به‌طور خودکار {{domxref("document.open()")}} را فراخوانی می‌کند که سند را پاک می‌کند.

استثنا این است که اگر فراخوانی `document.write()` درون یک تگ `<script>` درون‌خطی HTML تعبیه شده باشد، به‌طور خودکار `document.open()` را فراخوانی نمی‌کند:

```html
<script>
  document.write("<h1>Main title</h1>");
</script>
```

`document.write()` (و {{domxref("document.writeln")}}) را نمی‌توان با XML یا XHTML استفاده کرد و تلاش برای انجام این کار یک استثنای `InvalidStateError` پرتاب می‌کند.
این مورد در صورت باز کردن یک فایل محلی با پسوند .xhtml یا برای هر سندی که با نوع MIME `application/xhtml+xml` سرو می‌شود، صادق است.
اطلاعات بیشتر در [پرسش‌های متداول XHTML کنسرسیوم وب (W3C)](https://www.w3.org/MarkUp/2004/xhtml-faq#docwrite) موجود است.

استفاده از `document.write()` در اسکریپت‌های [تأخیری (deferred)](/en-US/docs/Web/HTML/Reference/Elements/script#defer) یا [ناهمگام (asynchronous)](/en-US/docs/Web/HTML/Reference/Elements/script#async) نادیده گرفته می‌شود و پیامی مانند «A call to `document.write()` from an asynchronously-loaded external script was ignored» در کنسول خطا دریافت خواهید کرد.

فقط در مرورگر Edge، فراخوانی `document.write()` بیش از یک بار در یک {{HTMLElement("iframe")}} باعث خطای «SCRIPT70: Permission denied» می‌شود.

### ملاحظات امنیتی

این متد یک بردار احتمالی برای حملات [اسکریپت‌نویسی بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) است، جایی که رشته‌های بالقوه ناامن ارائه‌شده توسط کاربر بدون پاک‌سازی قبلی به DOM تزریق می‌شوند.
اگرچه این متد ممکن است در برخی مرورگرها از اجرای عناصر {{HTMLElement("script")}} در هنگام تزریق جلوگیری کند (برای کروم به [مداخله در برابر document.write()](https://developer.chrome.com/blog/removing-document-write/) مراجعه کنید)، اما در برابر بسیاری از روش‌های دیگری که مهاجمان می‌توانند HTML را برای اجرای جاوااسکریپت مخرب قالب‌بندی کنند، آسیب‌پذیر است.

می‌توانید این مسائل را با همیشه ارسال اشیاء {{domxref("TrustedHTML")}} به‌جای رشته‌ها و [اجباری کردن انواع مورد اعتماد](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) با استفاده از دستور CSP [`require-trusted-types-for`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/require-trusted-types-for) کاهش دهید.
این اطمینان می‌دهد که ورودی از یک تابع تبدیل عبور می‌کند که این فرصت را دارد تا ورودی را [پاک‌سازی](/en-US/docs/Web/Security/Attacks/XSS#sanitization) کند و نشانه‌گذاری بالقوه خطرناک (مانند عناصر {{htmlelement("script")}} و ویژگی‌های کنترل‌کننده رویداد) را قبل از تزریق حذف کند.

## مثال‌ها

### نوشتن TrustedHTML

این مثال از [API انواع مورد اعتماد (Trusted Types API)](/en-US/docs/Web/API/Trusted_Types_API) برای پاک‌سازی رشته‌های HTML از عناصر {{htmlelement("script")}} قبل از نوشتن در سند استفاده می‌کند.

مثال در ابتدا مقداری متن پیش‌فرض و یک دکمه نمایش می‌دهد.
هنگامی که دکمه کلیک می‌شود، سند فعلی باز می‌شود، سه رشته HTML به نمونه‌های {{domxref("TrustedHTML")}} تبدیل شده و در سند نوشته می‌شوند و سپس سند بسته می‌شود.
این کار سند موجود در قاب مثال، از جمله HTML اصلی دکمه و جاوااسکریپتی که به‌روزرسانی را انجام داده است، جایگزین می‌کند!

#### HTML

```html
<p>Some original document content.</p>
<button id="replace" type="button">Replace document content</button>
```

#### جاوااسکریپت

ابتدا از ویژگی {{domxref("Window.trustedTypes")}} برای دسترسی به {{domxref("TrustedTypePolicyFactory")}} سراسری استفاده می‌کنیم و از روش {{domxref("TrustedTypePolicyFactory/createPolicy","createPolicy()")}} آن برای تعریف خط‌مشی‌ای به نام `"docPolicy"` استفاده می‌کنیم.

خط‌مشی جدید یک تابع تبدیل `createHTML()` برای ایجاد اشیاء {{domxref("TrustedHTML")}} تعریف می‌کند که به متد `write()` ارسال خواهیم کرد.
این روش می‌تواند هر کاری که بخواهد با رشته ورودی انجام دهد: API انواع مورد اعتماد فقط از شما می‌خواهد که ورودی را از یک تابع تبدیل خط‌مشی عبور دهید، نه اینکه تابع تبدیل کار خاصی انجام دهد.

از این روش برای [پاک‌سازی](/en-US/docs/Web/Security/Attacks/XSS#sanitization) ورودی با حذف ویژگی‌های بالقوه ناامن مانند تگ‌های {{htmlelement("script")}} یا ویژگی‌های کنترل‌کننده رویداد استفاده می‌کنید.
پاک‌سازی درست انجام دادن آن دشوار است، بنابراین این فرآیند معمولاً از یک کتابخانه شخص ثالث معتبر مانند [DOMPurify](https://github.com/cure53/DOMPurify) استفاده می‌کند.

برای اهداف نمایش، در اینجا یک «پاک‌ساز» ابتدایی پیاده‌سازی می‌کنیم که نماد `<` را در تگ‌های باز و بسته اسکریپت با کاراکتر `&lt;` جایگزین می‌کند.

```js
const policy = trustedTypes.createPolicy("docPolicy", {
  createHTML(string) {
    return string
      .replace("<script", "&lt;script")
      .replace("</script", "&lt;/script");
  },
});
```

سپس می‌توانیم از روش {{domxref("TrustedTypePolicy.createHTML()")}} روی خط‌مشی بازگشتی برای ایجاد اشیاء {{domxref("TrustedHTML")}} از رشته‌های ورودی اصلی خود استفاده کنیم.
این اشیاء زمانی که کاربر دکمه را کلیک می‌کند به تابع `write()` ارسال می‌شوند.

```js
const oneInput = "<h1>Out with the old</h1>";
const twoInput = "<p>in with the new!</p>";
const threeInput = "<script>alert('evil afoot')<" + "/script>";
const replace = document.querySelector("#replace");

replace.addEventListener("click", () => {
  document.open();
  document.write(
    policy.createHTML(oneInput),
    policy.createHTML(twoInput),
    policy.createHTML(threeInput),
  );
  document.close();
});
```

#### نتیجه

دکمه را فشار دهید و توجه کنید که عناصر HTML که به آن‌ها اعتماد داریم (در این مثال) تزریق می‌شوند، اما عنصر ناامن {{htmlelement("script")}} به‌صورت متن ساده نمایش داده می‌شود.

{{EmbedLiveSample("Writing TrustedHTML")}}

### نوشتن رشته‌ها

این مثال همانند مثال قبلی است، با این تفاوت که انواع مورد اعتماد استفاده یا اعمال نمی‌شوند.
ما رشته‌های پاک‌سازی‌نشده می‌نویسیم که ممکن است مسیری برای [حملات XSS](/en-US/docs/Web/Security/Attacks/XSS) فراهم کنند.

مثال در ابتدا مقداری متن پیش‌فرض و یک دکمه نمایش می‌دهد.
هنگامی که دکمه کلیک می‌شود، سند فعلی باز می‌شود، سه رشته HTML در سند نوشته می‌شوند و سپس سند بسته می‌شود.
این کار سند موجود در قاب مثال، از جمله HTML اصلی دکمه و جاوااسکریپتی که به‌روزرسانی را انجام داده است، جایگزین می‌کند.

#### HTML

```html
<p>Some original document content.</p>
<button id="replace" type="button">Replace document content</button>
```

#### جاوااسکریپت

```js
const replace = document.querySelector("#replace");

const oneInput = "<h1>Out with the old</h1>";
const twoInput = "<p>in with the new!</p>";
const threeInput = "<script>alert('evil afoot')<" + "/script>";

replace.addEventListener("click", () => {
  document.open();
  document.write(oneInput, twoInput, threeInput);
  document.close();
});
```

#### نتیجه

دکمه را فشار دهید و توجه کنید که همه عناصر HTML تزریق می‌شوند.
این شامل عنصر {{htmlelement("script")}} نیز می‌شود که در یک برنامه واقعی ممکن است کدهای مخرب را اجرا کرده باشد.

{{EmbedLiveSample("Writing strings")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("document.writeln()")}}
- {{domxref("element.innerHTML")}}
- {{domxref("document.createElement()")}}
- [API انواع مورد اعتماد (Trusted Types API)](/en-US/docs/Web/API/Trusted_Types_API)
- [اسکریپت‌نویسی بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS)