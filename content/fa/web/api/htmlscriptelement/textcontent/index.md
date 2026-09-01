---
title: "HTMLScriptElement: textContent property"
short-title: textContent
slug: Web/API/HTMLScriptElement/textContent
page-type: web-api-instance-property
browser-compat: api.HTMLScriptElement.textContent
---

{{APIRef("DOM")}}

> [!WARNING]
> این ویژگی محتوای متنی یک عنصر اسکریپت را نشان می‌دهد که ممکن است بسته به نوع اسکریپت قابل اجرا باشد. APIهایی مانند این به عنوان [حفره‌های تزریق](/en-US/docs/Web/API/Trusted_Types_API#concepts_and_usage) شناخته می‌شوند و به طور بالقوه بردار حمله‌های [کراس‌سایت اسکریپتینگ (XSS)](/en-US/docs/Web/Security/Attacks/XSS) هستند.
>
> می‌توانید این خطر را با اختصاص دادن همیشه اشیاء {{domxref("TrustedScript")}} به جای رشته‌ها و [اجباری کردن انواع قابل اعتماد](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) کاهش دهید. برای اطلاعات بیشتر به [ملاحظات امنیتی](#security_considerations) مراجعه کنید.

ویژگی **`textContent`** از رابط {{domxref("HTMLScriptElement")}} محتوای متنی درون‌خطی عنصر {{HTMLElement("script")}} را نشان می‌دهد. این ویژگی مشابه ویژگی‌های {{domxref("HTMLScriptElement.text","text")}} و {{domxref("HTMLScriptElement.innerText","innerText")}} عمل می‌کند.

## مقدار

دریافت ویژگی یک رشته حاوی متن اسکریپت را برمی‌گرداند.

تنظیم ویژگی یک شیء {{domxref("TrustedScript")}} یا یک رشته را می‌پذیرد.

### استثناها

- `TypeError`
  - : زمانی پرتاب می‌شود که ویژگی با یک رشته تنظیم شود در حالی که [انواع قابل اعتماد](/en-US/docs/Web/API/Trusted_Types_API) توسط [CSP اجباری شده‌اند](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) و هیچ سیاست پیش‌فرضی تعریف نشده باشد.

## توضیحات

ویژگی **`textContent`** از رابط {{domxref("HTMLScriptElement")}} محتوای متنی داخل عنصر {{HTMLElement("script")}} را نشان می‌دهد.

برای یک اسکریپت قابل اجرا (یعنی اسکریپتی که {{domxref('HTMLScriptElement/type','type')}} آن نشان می‌دهد که یک اسکریپت ماژول یا کلاسیک است)، این متن یک کد قابل اجرای درون‌خطی است. برای انواع دیگر، ممکن است یک نقشه واردات، قوانین حدس و گمان، یا نوع دیگری از بلوک داده را نشان دهد.

توجه داشته باشید که اگر ویژگی {{domxref('HTMLScriptElement/src','src')}} تنظیم شود، محتوای ویژگی `textContent` نادیده گرفته می‌شود.

ویژگی `textContent` همچنین روی {{domxref("Node.textContent","Node")}} تعریف شده است و بنابراین می‌تواند با گره‌ها (و عناصر) دیگر استفاده شود. هنگامی که با عناصر دیگر استفاده می‌شود، انتظار یا اجبار اختصاص یک {{domxref("TrustedScript")}} را ندارد.

### ملاحظات امنیتی

ویژگی `textContent` — و ویژگی‌های مشابه `text` و `innerText` — یک بردار احتمالی برای حملات [کراس‌سایت اسکریپتینگ (XSS)](/en-US/docs/Web/Security/Attacks/XSS) هستند، جایی که رشته‌های بالقوه ناایمن ارائه شده توسط کاربر اجرا می‌شوند. به عنوان مثال، مثال زیر فرض می‌کند که `scriptElement` یک عنصر `<script>` قابل اجرا است و `untrustedCode` توسط یک کاربر ارائه شده است:

```js
const untrustedCode = "alert('Potentially evil code!');";
scriptElement.textContent = untrustedCode; // هشدار را نشان می‌دهد
```

می‌توانید این مشکلات را با اختصاص دادن همیشه اشیاء {{domxref("TrustedScript")}} به جای رشته‌ها و [اجباری کردن انواع قابل اعتماد](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) با استفاده از دستورالعمل CSP [`require-trusted-types-for`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/require-trusted-types-for) کاهش دهید. این اطمینان می‌دهد که ورودی از یک تابع تبدیل عبور می‌کند، که شانس [پالایش](/en-US/docs/Web/Security/Attacks/XSS#sanitization) یا رد متن قبل از تزریق را دارد.

رفتار تابع تبدیل به مورد استفاده خاصی که نیاز به یک اسکریپت ارائه شده توسط کاربر دارد بستگی دارد. در صورت امکان، باید اسکریپت‌های مجاز را دقیقاً به کدی که به اجرای آن اعتماد دارید محدود کنید. اگر این امکان‌پذیر نیست، می‌توانید استفاده از توابع خاصی را درون رشته ارائه شده مجاز یا مسدود کنید.

## مثال‌ها

### استفاده از TrustedScript

برای کاهش خطر XSS، باید همیشه نمونه‌های `TrustedScript` را به ویژگی `textContent` اختصاص دهیم.

انواع قابل اعتماد هنوز در همه مرورگرها پشتیبانی نمی‌شوند، بنابراین ابتدا [tinyfill انواع قابل اعتماد](/en-US/docs/Web/API/Trusted_Types_API#trusted_types_tinyfill) را تعریف می‌کنیم. این به عنوان یک جایگزین شفاف برای API جاوااسکریپت انواع قابل اعتماد عمل می‌کند:

```js
if (typeof trustedTypes === "undefined")
  trustedTypes = { createPolicy: (n, rules) => rules };
```

سپس یک {{domxref("TrustedTypePolicy")}} ایجاد می‌کنیم که یک متد {{domxref("TrustedTypePolicy/createScript", "createScript()")}} برای تبدیل رشته‌های ورودی به نمونه‌های {{domxref("TrustedScript")}} تعریف می‌کند. برای هدف این مثال، دقیقاً همان اسکریپتی را که نیاز داریم مجاز می‌کنیم.

```js
const policy = trustedTypes.createPolicy("inline-script-policy", {
  createScript(input) {
    // در اینجا مشخص کنید کدام اسکریپت‌ها ایمن هستند
    if (input === "const num = 10;\nconsole.log(num)") {
      return input; // این اسکریپت دقیق را مجاز کن
    }
    throw new TypeError(`اسکریپت غیرقابل اعتماد مسدود شد: ${input}`);
  },
});
```

سپس عنصر اسکریپتی را که مقدار را به آن اختصاص می‌دهیم ایجاد می‌کنیم و یک دستگیره به عنصر می‌گیریم.

```html
<script id="el"></script>
```

```js
// عنصر اسکریپتی را که کد را به آن تزریق می‌کنیم دریافت کنید
const el = document.getElementById("el");
```

سپس از شیء `policy` برای ایجاد یک شیء `trustedScript` از رشته ورودی بالقوه ناایمن استفاده می‌کنیم و نتیجه را به عنصر اختصاص می‌دهیم:

```js
// رشته بالقوه مخرب
const untrustedScriptOne = "const num = 10;\nconsole.log(num)";

// ایجاد یک نمونه TrustedScript با استفاده از سیاست
const trustedScript = policy.createScript(untrustedScriptOne);

// تزریق TrustedScript (که حاوی یک رشته قابل اعتماد است)
el.textContent = trustedScript;
```

### مقایسه `textContent`، `text` و `innerText`

این مثال نشان می‌دهد که اختصاص یک اسکریپت به هر یک از ویژگی‌های متنی، مانند `textContent`، منجر به خواندن همان مقدار از همه ویژگی‌های متنی می‌شود.

توجه داشته باشید که در این مورد از سیاست برای ایجاد اسکریپت‌های قابل اعتماد استفاده نمی‌کنیم (برای اختصار فرض می‌کنیم که رشته‌های ارائه شده قابل اعتماد هستند).

```js
// تنظیم ویژگی textContent
el.textContent = "console.log(10);";

console.log(`textContent: ${el.textContent}`);
// "textContent: console.log(10);"

console.log(`text: ${el.text}`);
// "text: console.log(10);"

console.log(`innerText: ${el.innerText}`);
// "innerText: console.log(10);"

// تنظیم ویژگی text
el.text = "const num = 10;\nconsole.log(num)";

console.log(`textContent: ${el.textContent}`);
// textContent: const num = 10; console.log(num)"

console.log(`text: ${el.text}`);
// "text: const num = 10; console.log(num)"

console.log(`innerText: ${el.innerText}`);
// "innerText: const num = 10; console.log(num)"

// تنظیم ویژگی innerText
el.innerText = "const num = 10;alert('Help')";

console.log(`textContent: ${el.textContent}`);
// textContent: const num = 10;alert('Help')"

console.log(`text: ${el.text}`);
// "text: const num = 10;alert('Help')"

console.log(`innerText: ${el.innerText}`);
// "innerText: const num = 10;alert('Help')"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLScriptElement.text","text")}}
- {{domxref("HTMLScriptElement.innerText","innerText")}}