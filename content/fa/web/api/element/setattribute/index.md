---
title: "Element: setAttribute() method"
short-title: setAttribute()
slug: Web/API/Element/setAttribute
page-type: web-api-instance-method
browser-compat: api.Element.setAttribute
---

{{APIRef("DOM")}}

> [!WARNING]
> این متد می‌تواند مقادیر ویژگی‌هایی را بپذیرد که بسته به نوع ویژگی، به‌صورت HTML، اسکریپت یا URL اسکریپت تجزیه می‌شوند.
> چنین APIهایی به‌عنوان [injection sinks](/en-US/docs/Web/API/Trusted_Types_API#concepts_and_usage) شناخته می‌شوند و اگر مقدار در اصل از سوی یک مهاجم آمده باشد، می‌توانند بستری برای حملات [cross-site scripting (XSS)](/en-US/docs/Web/Security/Attacks/XSS) باشند.
>
> می‌توانید این خطر را با همیشه ارسال شیء نوع مورد اعتماد مناسب ({{domxref("TrustedHTML")}}، {{domxref("TrustedScript")}} یا {{domxref("TrustedScriptURL")}}) به‌جای رشته‌ها برای آن دسته از ویژگی‌هایی که به این نوع‌ها نیاز دارند، و با [اجبار کردن trusted types](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) کاهش دهید.
> برای اطلاعات بیشتر به [ملاحظات امنیتی](#security_considerations) مراجعه کنید.

متد **`setAttribute()`** در رابط {{domxref("Element")}} مقدار یک ویژگی را روی عنصر مشخص‌شده تنظیم می‌کند.
اگر ویژگی از قبل وجود داشته باشد، مقدار آن به‌روزرسانی می‌شود؛ در غیر این صورت، ویژگی جدیدی با نام و مقدار مشخص‌شده اضافه می‌شود.

اگر لازم است قبل از افزودن، با گره {{domxref("Attr")}} کار کنید (مثلاً آن را از عنصر دیگری کپی کنید)، می‌توانید به‌جای آن از متد {{domxref("Element.setAttributeNode()", "setAttributeNode()")}} استفاده کنید.

## سینتکس

```js-nolint
setAttribute(qualifiedName, value)
```

### پارامترها

- `qualifiedName`
  - : رشته‌ای شامل نام کامل (qualified name) ویژگی‌ای که قرار است مقدار آن تنظیم شود.
    وقتی `setAttribute()` روی یک عنصر HTML در یک سند HTML فراخوانی شود، نام ویژگی به‌طور خودکار به حروف کوچک تبدیل می‌شود.

    قالب نام کامل به‌صورت `prefix:localName` یا `localName` است که اجزای آن چنین تعریف می‌شوند:
    - `prefix` {{optional_inline}}
      - : «نام مستعار کوتاه» برای فضای نام، همان‌طور که توسط ویژگی {{DOMxRef("Attr.prefix", "prefix")}} بازگردانده می‌شود.
    - `localName`
      - : نام محلی ویژگی، همان‌طور که توسط ویژگی {{DOMxRef("Attr.localName", "localName")}} بازگردانده می‌شود.

- `value`
  - : یک نوع مورد اعتماد (trusted type) یا رشته‌ای حاوی مقداری که به ویژگی اختصاص داده می‌شود.

    وقتی trusted types اجباری شده باشند، برای ویژگی‌های زیر باید نمونه‌های نوع مورد اعتماد ارسال شود:
    - ویژگی‌های محتوایی مدیریت رویداد (event handler)، مانند `onclick` و `onload`، به یک {{domxref("TrustedScript")}} نیاز دارند.
    - {{domxref("HTMLIFrameElement.srcdoc")}} به یک نمونه {{domxref("TrustedHTML")}} نیاز دارد.
    - {{domxref("HTMLScriptElement.src")}} به یک نمونه {{domxref("TrustedScriptURL")}} نیاز دارد.
    - {{domxref("SVGScriptElement.href")}} به یک نمونه {{domxref("TrustedScriptURL")}} نیاز دارد.

    برای سایر ویژگی‌ها trusted types اجباری نیستند، بنابراین می‌توان یک رشته یا هر نوع مورد اعتمادی ارسال کرد.

    اگر مقدار مشخص‌شده رشت‌ای نباشد، به‌طور خودکار به رشته تبدیل می‌شود.

    ویژگی‌های بولی اگر در عنصر حضور داشته باشند، مقدار `true` در نظر گرفته می‌شوند.
    باید `value` را به رشته خالی (`""`) یا نام ویژگی تنظیم کنید، بدون فاصله‌های ابتدایی یا انتهایی.
    برای یک نمایش عملی، [نمونه](#examples) را در پایین ببینید.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `InvalidCharacterError` {{domxref("DOMException")}}
  - : اگر [`prefix`](#prefix) یا [`localName`](#localname) نامعتبر باشد پرتاب می‌شود:
    - `prefix` باید حداقل یک نویسه داشته باشد و نمی‌تواند شامل فاصله‌های خالی ASCII، `NULL`، `/` یا `>` باشد (به‌ترتیب U+0000، U+002F یا U+003E).
    - `localName` باید حداقل یک نویسه داشته باشد و نمی‌تواند شامل فاصله‌های خالی ASCII، `NULL`، `/`، `=` یا `>` باشد (به‌ترتیب U+0000، U+002F، U+003D یا U+003E).

    > [!NOTE]
    > نسخه‌های قبلی مشخصات محدودکننده‌تر بودند و لازم داشتند که `qualifiedName` یک [نام XML](https://www.w3.org/TR/xml/#dt-name) معتبر باشد.

- `TypeError`
  - : اگر برای [`value`](#value) به‌جای شیء نوع مورد اعتماد (برای آن دسته از ویژگی‌هایی که به آن نیاز دارند) یک رشته ارسال شود، در حالی که [Trusted Types](/en-US/docs/Web/API/Trusted_Types_API) توسط [یک CSP اجباری شده](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) باشند و هیچ سیاست پیش‌فرضی تعریف نشده باشد، پرتاب می‌شود.

## توضیحات

متد **`setAttribute()`** مقدار یک ویژگی را روی عنصر مشخص‌شده تنظیم می‌کند.
اگر ویژگی از قبل وجود داشته باشد، مقدار آن به‌روزرسانی می‌شود؛ در غیر این صورت، ویژگی جدیدی با نام و مقدار مشخص‌شده اضافه می‌شود.

برای تنظیم مقدار یک ویژگی بولی مانند `disabled`، می‌توانید هر مقداری را مشخص کنید.
فرقی نمی‌کند از چه مقداری استفاده کنید؛ اگر ویژگی حضور داشته باشد، مقدار آن `true` در نظر گرفته می‌شود.
طبق قرارداد، ویژگی‌های بولی را با تنظیم مقدارشان روی نام خود ویژگی یا رشته خالی (`""`) فعال می‌کنیم.
نبودِ یک ویژگی بولی به این معنی است که مقدار آن `false` است؛ برای «خنثی کردن» اثر فعال‌سازی یک ویژگی بولی باید {{domxref("Element.removeAttribute()")}} را فراخوانی کنید.

برای دریافت مقدار فعلی یک ویژگی از {{domxref("Element.getAttribute", "getAttribute()")}} استفاده کنید؛ برای حذف یک ویژگی، {{domxref("Element.removeAttribute", "removeAttribute()")}} را فراخوانی کنید.

### ملاحظات امنیتی

[برخی از ویژگی‌ها](#value) می‌توانند به‌عنوان بستری برای حملات [cross-site scripting (XSS)](/en-US/docs/Web/Security/Attacks/XSS) استفاده شوند؛ جایی که رشته‌های بالقوه ناامن ارائه‌شده توسط کاربر، بدون اینکه ابتدا پاک‌سازی شوند، به DOM تزریق می‌شوند، یا اسکریپت‌هایی اجرا می‌شوند که ممکن است حاوی کد مخرب باشند.

برای مثال، کد زیر نشان می‌دهد که چگونه یک رشته بالقوه غیرقابل اعتماد ارائه‌شده توسط کاربر، هنگام فشردن دکمه اجرا می‌شود.

```js
const button = document.querySelector("button");
const potentiallyUnsafeString = "alert(1)";
button.setAttribute("onclick", potentiallyUnsafeString);
```

به‌طور مشابه، می‌توانید HTML غیرقابل اعتماد را با تنظیم ویژگی {{domxref("HTMLIFrameElement.srcdoc")}} به DOM تزریق کنید، یا یک URL غیرقابل اعتماد به ویژگی‌های {{domxref("HTMLScriptElement.src")}} یا {{domxref("SVGScriptElement.href")}} بدهید.

می‌توانید این مشکلات را با همیشه اختصاص دادن شیء نوع مورد اعتماد مناسب ({{domxref("TrustedHTML")}}، {{domxref("TrustedScript")}} یا {{domxref("TrustedScriptURL")}}) به هر ویژگی به‌جای رشته‌ها، و با [اجبار کردن trusted types](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) با استفاده از دستور CSP [`require-trusted-types-for`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/require-trusted-types-for) کاهش دهید.
این کار تضمین می‌کند که ورودی از یک تابع تبدیل عبور کند که ممکن است برای مثال، قبل از تزریق، نشانه‌گذاری بالقوه خطرناک را از HTML حذف کند.

## نمونه‌ها

### تنظیم ویژگی‌های امن

این مثال از `setAttribute()` برای تنظیم ویژگی‌های `name` و `disabled` روی یک {{HTMLElement("button")}} استفاده می‌کند.
هر دوی این ویژگی‌ها از نظر XSS امن هستند.
از آنجا که مقادیر آن‌ها به‌عنوان HTML در DOM اجرا یا تجزیه نمی‌شوند، نیازی به ارسال trusted types نداریم.

#### HTML

```html
<div>
  <button id="reset" type="button">Reset</button>
  <button id="toggle_disabled">Toggle</button>
</div>
<button id="hello_button">Some Text</button>
```

```css hidden
button {
  height: 30px;
  width: 100px;
  margin: 1em;
}
```

#### JavaScript

ابتدا عنصر button را می‌گیریم و ویژگی `name` آن را با استفاده از `setAttribute()` روی `"helloButton"` تنظیم می‌کنیم.
برای نشان دادن اینکه نام ویژگی تغییر کرده است، سپس متن ویژگی را می‌گیریم و روی دکمه نمایش می‌دهیم.

```js
const helloButton = document.querySelector("#hello_button");
helloButton.setAttribute("name", "helloButton");

// Set button text to name to show the attribute changed
helloButton.innerText = helloButton.getAttribute("name");
```

این کد مربوط به دکمه «Reset» است.
این دکمه صرفاً صفحه را دوباره بارگذاری می‌کند.

```js
const reloadButton = document.querySelector("#reset");
reloadButton.addEventListener("click", () => document.location.reload());
```

در ادامه نشان می‌دهیم که چگونه یک ویژگی بولی را تنظیم و بازنشانی کنیم.
وقتی روی دکمه «Toggle» کلیک می‌شود، بررسی می‌کنیم که آیا خاصیت بولی `disabled` تعریف شده است (این خاصیت، ویژگی `disabled` را بازتاب می‌دهد و اگر دکمه غیرفعال باشد `true` و در غیر این صورت `false` است).
اگر دکمه غیرفعال باشد، {{domxref("Element.removeAttribute()")}} را فراخوانی می‌کنیم تا ویژگی حذف شود و در نتیجه دکمه فعال شود.
اگر دکمه فعال باشد، با تنظیم ویژگی `disabled` روی `"disabled"` آن را غیرفعال می‌کنیم.

```js
const toggleDisabledButton = document.querySelector("#toggle_disabled");

toggleDisabledButton.addEventListener("click", () => {
  if (helloButton.disabled) {
    // Button is disabled. Enable by removing attribute
    helloButton.removeAttribute("disabled");
  } else {
    // Button enabled. Disable by setting value to anything
    // (normally "" or "disabled")
    helloButton.setAttribute("disabled", "disabled");
  }
});
```

#### نتایج

نمونه در حال اجرا در زیر نشان داده شده است.
می‌بینید که متن دکمه پایینی «helloButton» است؛ زیرا خاصیت `name` را تنظیم کردیم و سپس از آن برای تنظیم متن دکمه استفاده شد.
می‌توانید دکمه «Toggle» را فشار دهید تا «helloButton» غیرفعال یا فعال شود.

{{ EmbedLiveSample('Setting safe attributes', '300', '150') }}

### تنظیم ویژگی‌های ناامن

در این مثال نشان می‌دهیم که چگونه می‌توانید خطرات فراخوانی `setAttributes()` را برای تنظیم ویژگی {{domxref("HTMLIFrameElement.srcdoc", "srcdoc")}} روی یک {{htmlelement("iframe")}} کاهش دهید.
این ویژگی، HTML منبع یک فریم را تنظیم می‌کند و بنابراین می‌تواند کد بالقوه غیرقابل اعتماد یا ناامن را به DOM تزریق کند.

روش کار برای تنظیم {{domxref("HTMLScriptElement.src","src")}} روی عناصر اسکریپت HTML، {{domxref("SVGScriptElement.href","href")}} روی عناصر اسکریپت SVG و ویژگی‌های مدیریت رویداد `onXxxx` مشابه خواهد بود؛ تفاوت اصلی این است که اشیاء نوع مورد اعتماد متفاوتی به آن‌ها ارسال می‌کنید.

Trusted types هنوز در همه مرورگرها پشتیبانی نمی‌شوند، بنابراین ابتدا [trusted types tinyfill](/en-US/docs/Web/API/Trusted_Types_API#trusted_types_tinyfill) را تعریف می‌کنیم.
این کد به‌عنوان جایگزینی شفاف برای API جاوااسکریپت Trusted Types عمل می‌کند:

```js
if (typeof trustedTypes === "undefined")
  trustedTypes = { createPolicy: (n, rules) => rules };
```

سپس یک {{domxref("TrustedTypePolicy")}} ایجاد می‌کنیم که یک {{domxref("TrustedTypePolicy/createHTML", "createHTML()")}} برای تبدیل رشته ورودی به نمونه‌های {{domxref("TrustedHTML")}} تعریف می‌کند.
معمولاً پیاده‌سازی‌های `createHTML()` از کتابخانه‌ای مانند [DOMPurify](https://github.com/cure53/DOMPurify) برای پاک‌سازی ورودی استفاده می‌کنند، همان‌طور که در زیر نشان داده شده است:

```js
const policy = trustedTypes.createPolicy("my-policy", {
  createHTML: (input) => DOMPurify.sanitize(input),
});
```

سپس از این شیء `policy` برای ایجاد یک شیء `TrustedHTML` از رشته ورودی بالقوه ناامن استفاده می‌کنیم و نتیجه را به عنصر اختصاص می‌دهیم:

```js
// The potentially malicious string
const untrustedString = "<p>I might be XSS</p><img src='x' onerror='alert(1)'>";

// Create a TrustedHTML instance using the policy
const trustedHTML = policy.createHTML(untrustedString);

// Inject the TrustedHTML (which contains a trusted string)
const iframeElement = document.querySelector("#an_iframe");
iframeElement.setAttribute("srcdoc", trustedHTML);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Element.hasAttribute()")}}
- {{domxref("Element.getAttribute()")}}
- {{domxref("Element.removeAttribute()")}}
- {{domxref("Element.toggleAttribute()")}}