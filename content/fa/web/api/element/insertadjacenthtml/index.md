---
title: "Element: insertAdjacentHTML() method"
short-title: insertAdjacentHTML()
slug: Web/API/Element/insertAdjacentHTML
page-type: web-api-instance-method
browser-compat: api.Element.insertAdjacentHTML
---

{{APIRef("DOM")}}

> [!WARNING]
> این متد ورودی خود را به‌عنوان HTML یا XML تجزیه می‌کند و نتیجه را در DOM می‌نویسد.
> چنین APIهایی به‌عنوان [زبانِ تزریق (injection sinks)](/en-US/docs/Web/API/Trusted_Types_API#concepts_and_usage) شناخته می‌شوند و اگر ورودی در اصل از سوی یک مهاجم بوده باشد، به‌طور بالقوه می‌توانند بستری برای حملات [اسکریپت‌نویسی میان‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) باشند.
>
> می‌توانید با اختصاص دادن اشیاء {{domxref("TrustedHTML")}} به‌جای رشته‌ها و [اجبارِ انواع قابل‌اعتماد](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) با استفاده از دستور CSP مربوط به [`require-trusted-types-for`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/require-trusted-types-for) این خطر را کاهش دهید.
> این کار تضمین می‌کند که ورودی از یک تابع تبدیل عبور داده می‌شود و این تابع فرصت [پاک‌سازی](/en-US/docs/Web/Security/Attacks/XSS#sanitization) ورودی برای حذف نشانه‌گذاری‌های بالقوه خطرناک مانند عناصر {{htmlelement("script")}} و ویژگی‌های رویدادhandler را دارد.

متد **`insertAdjacentHTML()`** از رابط {{domxref("Element")}}، ورودی مشخص‌شده را به‌عنوان HTML یا XML تجزیه می‌کند و گره‌های حاصل را در موقعیتی مشخص در درخت DOM درج می‌کند.

## نحو (Syntax)

```js-nolint
insertAdjacentHTML(position, input)
```

### پارامترها

- `position`
  - : رشته‌ای که موقعیت را نسبت به عنصر مشخص می‌کند. باید یکی از رشته‌های زیر باشد:
    - `"beforebegin"`
      - : قبل از عنصر. فقط زمانی معتبر است که عنصر در درخت DOM باشد و عنصر والد داشته باشد.
    - `"afterbegin"`
      - : دقیقاً داخل عنصر، قبل از اولین فرزند آن.
    - `"beforeend"`
      - : دقیقاً داخل عنصر، بعد از آخرین فرزند آن.
    - `"afterend"`
      - : بعد از عنصر. فقط زمانی معتبر است که عنصر در درخت DOM باشد و عنصر والد داشته باشد.
- `input`
  - : یک نمونه یا رشته {{domxref("TrustedHTML")}} که HTML یا XML مورد نظر برای تجزیه را تعریف می‌کند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها (Exceptions)

این متد ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر ایجاد کند:

- `NoModificationAllowedError` {{domxref("DOMException")}}
  - : اگر `position` برابر با `"beforebegin"` یا `"afterend"` باشد و عنصر یا والد نداشته باشد یا والد آن شیء `Document` باشد، پرتاب می‌شود.
- `SyntaxError` {{domxref("DOMException")}}
  - : اگر:
    - `position` یکی از چهار مقدار ذکرشده نباشد.
    - ورودی، XML باشد که خوش‌فرم (well-formed) نیست.
- `TypeError`
  - : اگر [انواع قابل‌اعتماد (Trusted Types)](/en-US/docs/Web/API/Trusted_Types_API) توسط [CSP](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) [اجبار شده باشند](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) و هیچ سیاست پیش‌فرضی تعریف نشده باشد، و ویژگی با یک رشته مقداردهی شود، پرتاب می‌شود.

## توضیحات

متد `insertAdjacentHTML()` عنصری را که روی آن استفاده می‌شود دوباره تجزیه نمی‌کند و به این ترتیب عناصر موجود درون آن عنصر را خراب نمی‌کند. این کار از گام اضافی سریال‌سازی جلوگیری می‌کند و باعث می‌شود این روش بسیار سریع‌تر از دستکاری مستقیم {{domxref("Element.innerHTML", "innerHTML")}} باشد.

اگر `<p>` عنصر موردنظر باشد، موقعیت‌های ممکن برای درج محتوای «foo» را می‌توان به صورت زیر مشاهده کرد:

```html
<!-- beforebegin -->
<p>
  <!-- afterbegin -->
  foo
  <!-- beforeend -->
</p>
<!-- afterend -->
```

این متد هیچ رفتار خاصی برای عناصر {{htmlelement("template")}} ندارد.
در بیشتر موارد، توسعه‌دهندگان باید به‌جای دستکاری مستقیم گره‌های فرزند یک عنصر template، از `insertAdjacentHTML()` روی ویژگی {{domxref("HTMLTemplateElement/content","content")}} آن template استفاده کنند.

### ملاحظات امنیتی

این متد هیچ پاک‌سازی‌ای برای حذف عناصر ناامن از نظر XSS مانند {{htmlelement("script")}} یا ویژگی‌های محتوایی رویداد (event handler content attributes) انجام نمی‌دهد.

هنگام درج HTML در یک صفحه با استفاده از `insertAdjacentHTML()`، باید به‌جای رشته‌ها، اشیاء {{domxref("TrustedHTML")}} ارسال کنید و [انواع قابل‌اعتماد را با CSP](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) و دستور [`require-trusted-types-for`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/require-trusted-types-for) [اجبار کنید](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types).
این کار تضمین می‌کند که ورودی از یک تابع تبدیل عبور داده می‌شود و این تابع فرصت [پاک‌سازی](/en-US/docs/Web/Security/Attacks/XSS#sanitization) ورودی برای حذف نشانه‌گذاری‌های بالقوه خطرناک قبل از تزریق را دارد.

زمانی که می‌دانید محتوای ارائه‌شده توسط کاربر باید متن ساده باشد، باید از متد {{domxref("Element.insertAdjacentText()")}} یا {{domxref("Node.textContent")}} استفاده کنید.
این کار ورودی را به‌صورت متن خام درج می‌کند و آن را به‌عنوان HTML تجزیه نمی‌کند.

## مثال‌ها

### درج HTML

این مثال چهار موقعیت درج را نشان می‌دهد.
همه متن‌های درج‌شده پررنگ هستند، در حالی که متنی که داخل عنصر درج می‌شود با رنگ قرمز و به‌صورت تک‌فاصله (code) استایل‌دهی می‌شود.

#### HTML

```html
<select id="position">
  <option>beforebegin</option>
  <option>afterbegin</option>
  <option>beforeend</option>
  <option>afterend</option>
</select>

<button id="insert">Insert HTML</button>
<button id="reset">Reset</button>

<p>
  Some text, with a <code id="subject">code-formatted element</code> inside it.
</p>
```

#### CSS

```css
code {
  color: red;
}
```

#### JavaScript

انواع قابل‌اعتماد هنوز در همه مرورگرها پشتیبانی نمی‌شوند، بنابراین ابتدا [جایگزین کوچک انواع قابل‌اعتماد (trusted types tinyfill)](/en-US/docs/Web/API/Trusted_Types_API#trusted_types_tinyfill) را تعریف می‌کنیم.
این کار به‌عنوان جایگزینی شفاف برای API جاوااسکریپت Trusted Types عمل می‌کند:

```js
if (typeof trustedTypes === "undefined")
  trustedTypes = { createPolicy: (n, rules) => rules };
```

سپس یک سیاست با نام `some-content-policy` تعریف می‌کنیم تا اشیاء {{domxref("TrustedHTML")}} را از ورودی بسازد (همچنین باید `some-content-policy` را با CSP اجبار کنید).
کد برای اینکه این مثال بدون وابستگی به شخص ثالث کار کند، یک سیاست بدون عملیات (no-op) پیاده‌سازی می‌کند.
کد برنامه شما باید از یک کتابخانه شخص ثالث مانند «DOMPurify» برای برگرداندن محتوای پاک‌سازی‌شده از ورودی غیرقابل‌اعتماد استفاده کند.

```js
const policy = trustedTypes.createPolicy("some-content-policy", {
  createHTML(input) {
    return input; // این کار را در کد خودتان انجام ندهید!
    // به جایش چیزی مثل این انجام دهید:
    // return DOMPurify.sanitize(input);
  },
});

const unsafeText = "<strong>inserted text</strong>";
const trustedHTML = policy.createHTML(unsafeText);
```

کد باقی‌مانده، HTML قابل‌اعتماد را در موقعیت انتخابی نسبت به عنصر با شناسه `subject` درج می‌کند.

```js
const insert = document.querySelector("#insert");
insert.addEventListener("click", () => {
  const subject = document.querySelector("#subject");
  const positionSelect = document.querySelector("#position");
  subject.insertAdjacentHTML(positionSelect.value, trustedHTML);
});

const reset = document.querySelector("#reset");
reset.addEventListener("click", () => {
  document.location.reload();
});
```

#### نتیجه

{{EmbedLiveSample("Inserting HTML", 100, 100)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.insertAdjacentElement()")}}
- {{domxref("Element.insertAdjacentText()")}}
- {{domxref("XMLSerializer")}}: سریال‌سازی یک درخت DOM به رشته XML
- [API انواع قابل‌اعتماد (Trusted Types API)](/en-US/docs/Web/API/Trusted_Types_API)