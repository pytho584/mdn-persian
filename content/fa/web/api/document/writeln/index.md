---
title: "Document: writeln() method"
short-title: writeln()
slug: Web/API/Document/writeln
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.Document.writeln
---

{{ ApiRef("DOM") }}{{deprecated_header}}

> [!WARNING]
> این متد ورودی خود را به‌عنوان HTML تجزیه کرده و نتیجه را در DOM می‌نویسد.
> APIهایی از این دست به‌عنوان [چاهک‌های تزریق](/en-US/docs/Web/API/Trusted_Types_API#concepts_and_usage) شناخته می‌شوند و در صورتی که ورودی از سوی یک مهاجم باشد، می‌توانند بستری برای حملات [اسکریپت‌نویسی بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) باشند.
>
> می‌توانید این خطر را با همیشه ارسال اشیاء `TrustedHTML` به‌جای رشته‌ها و [اجباری کردن trusted types](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) کاهش دهید.
> برای اطلاعات بیشتر [ملاحظات امنیتی](#security_considerations) را ببینید.

متد **`writeln()`** از رابط {{domxref("Document")}} متن را در یک یا چند پارامتر از نوع {{domxref("TrustedHTML")}} یا رشته به یک جریان سند که توسط {{domxref("document.open()")}} باز شده است، همراه با یک کاراکتر خط جدید می‌نویسد.

## نحو

```js-nolint
writeln(markup)
writeln(markup, markup2)
writeln(markup, markup2, /* …, */ markupN)
```

### پارامترها

- `markup`، …، `markupN`
  - : اشیاء {{domxref("TrustedHTML")}} یا رشته‌هایی حاوی متنی که قرار است به سند نوشته شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : متد روی یک سند XML فراخوانی شده است، یا هنگامی فراخوانی شده که تجزیه‌کننده در حال اجرای یک سازنده عنصر سفارشی است.
- `TypeError`
  - : یک رشته به‌عنوان یکی از پارامترها ارسال شده است در حالی که [Trusted Types اجباری شده است](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) و [هیچ خط‌مشی پیش‌فرضی تعریف نشده است](/en-US/docs/Web/API/TrustedTypePolicyFactory/createPolicy#creating_a_default_policy) برای ایجاد اشیاء {{domxref("TrustedHTML")}}.

## توضیحات

این متد اساساً مشابه {{domxref("document.write()")}} است اما یک خط جدید اضافه می‌کند (اطلاعات موجود در مبحث مرتبط برای این متد نیز کاربرد دارد).
این خط جدید تنها در صورتی قابل مشاهده خواهد بود که درون عنصری تزریق شود که در آن خطوط جدید نمایش داده می‌شوند.
اطلاعات اضافی در {{domxref("document.write()")}} برای این متد نیز معتبر است.

### ملاحظات امنیتی

این متد یک بستر احتمالی برای حملات [اسکریپت‌نویسی بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) است، که در آن رشته‌های بالقوه ناایمن ارائه‌شده توسط کاربر بدون پالایش اولیه به DOM تزریق می‌شوند.
اگرچه در برخی مرورگرها ممکن است این متد از اجرای عناصر {{HTMLElement("script")}} هنگام تزریق جلوگیری کند (به [مداخله در برابر document.write()](https://developer.chrome.com/blog/removing-document-write/) برای Chrome مراجعه کنید)، اما در برابر بسیاری از راه‌های دیگری که مهاجمان می‌توانند از HTML برای اجرای جاوااسکریپت مخرب استفاده کنند، آسیب‌پذیر است.

می‌توانید این مسائل را با همیشه ارسال اشیاء {{domxref("TrustedHTML")}} به‌جای رشته‌ها و [اجباری کردن trusted types](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) با استفاده از دستور CSP [`require-trusted-types-for`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/require-trusted-types-for) کاهش دهید.
این کار تضمین می‌کند که ورودی از یک تابع تبدیل عبور می‌کند، که این فرصت را دارد تا ورودی را برای حذف نشانه‌گذاری‌های بالقوه خطرناک (مانند عناصر {{htmlelement("script")}} و ویژگی‌های مدیریت رویداد) [پالایش](/en-US/docs/Web/Security/Attacks/XSS#sanitization) کند، قبل از اینکه تزریق شود.

## مثال‌ها

### نوشتن TrustedHTML

این مثال از [API Trusted Types](/en-US/docs/Web/API/Trusted_Types_API) برای پالایش رشته‌های HTML قبل از نوشتن آن‌ها در یک سند استفاده می‌کند.
همیشه باید از trusted types برای ارسال رشته‌های غیرقابل اعتماد به APIهای ناایمن استفاده کنید.

مثال ابتدا مقداری متن پیش‌فرض و یک دکمه را نمایش می‌دهد.
هنگامی که دکمه کلیک می‌شود، سند جاری باز می‌شود، برخی رشته‌های HTML به نمونه‌های {{domxref("TrustedHTML")}} تبدیل شده و در سند نوشته می‌شوند، و سپس سند بسته می‌شود.
این کار سند را در فریم مثال، از جمله HTML اصلی دکمه و جاوااسکریپتی که به‌روزرسانی را انجام می‌دهد، جایگزین می‌کند.

#### HTML

```html
<p>مقداری محتوای اصلی سند.</p>
<button id="replace" type="button">جایگزینی محتوای سند</button>
```

#### جاوااسکریپت

ابتدا از ویژگی {{domxref("Window.trustedTypes")}} برای دسترسی به {{domxref("TrustedTypePolicyFactory")}} جهانی استفاده می‌کنیم، و از متد {{domxref("TrustedTypePolicyFactory/createPolicy","createPolicy()")}} آن برای تعریف یک خط‌مشی به نام `"docPolicy"` استفاده می‌کنیم.

خط‌مشی جدید یک تابع تبدیل `createHTML()` برای ایجاد اشیاء {{domxref("TrustedHTML")}} تعریف می‌کند که به متد `writeln()` ارسال خواهیم کرد.
این تابع می‌تواند هر کاری که می‌خواهد با رشته ورودی انجام دهد: API trusted types فقط نیاز دارد که ورودی را از یک تابع تبدیل خط‌مشی عبور دهید، نه اینکه تابع تبدیل کار خاصی انجام دهد.

از این تابع برای [پالایش](/en-US/docs/Web/Security/Attacks/XSS#sanitization) ورودی با حذف ویژگی‌های بالقوه ناایمن مانند برچسب‌های {{htmlelement("script")}} یا ویژگی‌های مدیریت رویداد استفاده می‌کنید.
پالایش به‌درستی کار دشواری است، بنابراین این فرآیند معمولاً از یک کتابخانه شخص ثالث معتبر مانند [DOMPurify](https://github.com/cure53/DOMPurify) استفاده می‌کند.

در اینجا یک «پالاینده» ابتدایی پیاده‌سازی می‌کنیم که نماد `<` را در برچسب‌های باز و بسته اسکریپت با کاراکتر `&lt;` جایگزین می‌کند.
رشته‌های تزریق‌شده در این مثال در واقع هیچ عنصر مضری ندارند، بنابراین این صرفاً برای نمایش است.

```js
const policy = trustedTypes.createPolicy("docPolicy", {
  createHTML(string) {
    return string
      .replace("<script", "&lt;script")
      .replace("</script", "&lt;/script");
  },
});
```

سپس می‌توانیم از متد {{domxref("TrustedTypePolicy.createHTML()")}} روی خط‌مشی بازگشتی برای ایجاد اشیاء {{domxref("TrustedHTML")}} از رشته‌های ورودی اصلی خود استفاده کنیم.
این اشیاء سپس به تابع `writeln()` ارسال می‌شوند وقتی کاربر روی دکمه کلیک می‌کند.

```js
const replace = document.querySelector("#replace");
const oneInput = "<h1>برو بیرون با";
const twoInput = "کهنه</h1>";
const threeInput = "<pre>بیا تو با";
const fourInput = "نو!</pre>";

replace.addEventListener("click", () => {
  document.open();
  document.writeln(policy.createHTML(oneInput));
  document.writeln(policy.createHTML(twoInput), policy.createHTML(threeInput));
  document.writeln(policy.createHTML(fourInput));
  document.close();
});
```

#### نتایج

روی دکمه کلیک کنید.
توجه کنید که پس از هر بار فراخوانی `writeln()` یک خط جدید اضافه می‌شود، اما این تنها درون عنصر {{htmlelement("pre")}} قابل مشاهده است زیرا طرح آن به‌طور پیش‌فرض فضای خالی را حفظ می‌کند.

{{EmbedLiveSample("Writing TrustedHTML")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}