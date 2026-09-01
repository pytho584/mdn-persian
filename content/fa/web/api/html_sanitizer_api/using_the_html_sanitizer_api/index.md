---
title: "Using the HTML Sanitizer API"
---

---
title: Using the HTML Sanitizer API
slug: Web/API/HTML_Sanitizer_API/Using_the_HTML_Sanitizer_API
page-type: guide
---

{{DefaultAPISidebar("HTML Sanitizer API")}}

[HTML Sanitizer API](/en-US/docs/Web/API/HTML_Sanitizer_API) روش‌هایی در اختیار توسعه‌دهندگان قرار می‌دهد که به آن‌ها امکان می‌دهد HTML غیرقابل اعتماد را به‌طور امن در یک {{domxref("Element")}}، {{domxref("ShadowRoot")}} یا {{domxref("Document")}} تزریق کنند. این API همچنین به توسعه‌دهندگان این انعطاف را می‌دهد که در صورت نیاز، موجودیت‌های HTML مجاز را محدودتر یا گسترده‌تر کنند.

## ایمن‌سازی پیش‌فرض ایمن

رایج‌ترین کاربرد این API، تزریق امن یک رشته‌ی ارائه‌شده توسط کاربر به یک {{domxref("Element")}} است. مگر اینکه رشته‌ی مورد تزریق واقعاً _نیاز_ به حاوی موجودیت‌های HTML ناامن داشته باشد، می‌توانید از {{domxref('Element.setHTML()')}} به‌عنوان جایگزینی مستقیم برای {{domxref("Element.innerHTML")}} استفاده کنید.

برای مثال، کد زیر تمام عناصر و ویژگی‌های ناامن در برابر XSS را از رشته‌ی ورودی حذف می‌کند (در این مورد عنصر {{htmlelement("script")}})، همچنین هر عنصری که طبق مشخصات HTML به‌عنوان فرزند عنصر هدف مجاز نیست:

```js
const untrustedString = "abc <script>alert(1)<" + "/script> def";
const someElement = document.getElementById("target");

// someElement.innerHTML = untrustedString;
someElement.setHTML(untrustedString);

console.log(someElement.innerHTML); // abc def
```

سایر روش‌های امن در برابر XSS، یعنی {{domxref('ShadowRoot.setHTML()')}} و {{domxref('Document/parseHTML_static','Document.parseHTML()')}}، به همین ترتیب استفاده می‌شوند.

## استفاده از پیکربندی sanitizer

به همه‌ی روش‌های پاکسازی می‌توان یک {{domxref('Sanitizer')}} یا {{domxref('SanitizerConfig')}} به‌عنوان ورودی داد؛ این پیکربندی مشخص می‌کند هنگام درج رشته‌های HTML، کدام عناصر، ویژگی‌ها و نظرات (comments) مجاز هستند یا باید حذف شوند.

{{domxref('Sanitizer')}} در اصل یک پوشه (wrapper) حول {{domxref('SanitizerConfig')}} است که برخی بهینه‌سازی‌ها و نرمال‌سازی‌ها را انجام می‌دهد تا استفاده، اشتراک‌گذاری و تغییر آن آسان‌تر و امن‌تر شود.

### استفاده از روش‌های ایمن با یک sanitizer

روش‌های امن در برابر XSS همیشه هر عنصر یا ویژگی HTML ناامن را حذف می‌کنند (همان‌طور که در [ایمن‌سازی پیش‌فرض ایمن](#safe_sanitization_by_default) در بالا توضیح داده شد).

می‌توانید یک sanitizer را به‌عنوان آرگومان دوم به روش‌های امن ارسال کنید تا همان تعداد موجودیت یا تعداد کمتری نسبت به پیکربندی پیش‌فرض مجاز شوند. برای مثال، اگر می‌دانید در بافت `someElement` زیر فقط عناصر {{htmlelement("p")}} و {{htmlelement("a")}} مورد انتظار هستند، می‌توانید یک پیکربندی sanitizer ایجاد کنید که فقط همین عناصر را مجاز بشمارد:

```js
const sanitizerOne = new Sanitizer({ elements: ["p", "a"] });
sanitizerOne.allowAttribute("href");
someElement.setHTML(untrustedString, { sanitizer: sanitizerOne });
```

### مجاز کردن پاکسازی ناامن

گاهی ممکن است بخواهید ورودی‌ای را تزریق کنید که نیاز به حاوی عناصر یا ویژگی‌های بالقوه ناامن دارد. در این مورد می‌توانید از یکی از روش‌های ناامن در برابر XSS این API استفاده کنید: {{domxref('Element.setHTMLUnsafe()')}}، {{domxref('ShadowRoot.setHTMLUnsafe()')}} و {{domxref('Document/parseHTMLUnsafe_static','Document.parseHTMLUnsafe()')}}.

برای کاهش نسبتاًِ ریسک، می‌توانید ابتدا sanitizer پیش‌فرض را بسازید که فقط عناصر امن در برابر XSS را مجاز می‌کند، و سپس فقط همان موجودیت‌های ناامنی را که در ورودی انتظار می‌رود مجاز کنید.

برای مثال، در sanitizer زیر همه‌ی عناصر امن مجاز هستند، و علاوه بر آن هندلر ناامن `onclick` را نیز روی عناصر `button` (فقط) مجاز می‌کنیم.

```js
const untrustedString = '<button onclick="alert(1)">Button text</button>';
const someElement = document.getElementById("target");

const sanitizerOne = new Sanitizer(); // Default sanitizer
sanitizerOne.allowElement({ name: "button", attributes: ["onclick"] });
someElement.setHTMLUnsafe(untrustedString, { sanitizer: sanitizerOne });
```

با این کد، `alert(1)` مجاز می‌شود و این پتانسیل وجود دارد که این ویژگی برای اهداف مخرب استفاده شود. با این حال می‌دانیم که همه‌ی سایر موجودیت‌های HTML ناامن در برابر XSS حذف شده‌اند، بنابراین فقط باید نگران این یک مورد باشیم و می‌توانیم تدابیر دیگری نیز اعمال کنیم.

روش‌های ناامن هر پیکربندی sanitizer را که ارائه دهید (یا هیچ) استفاده می‌کنند، بنابراین هنگام استفاده از آن‌ها باید احتیاط کنید. حداقل باید [Trusted Types](/en-US/docs/Web/API/HTML_Sanitizer_API#sanitization_and_trusted_types) را اعمال کنید و به‌جای رشته‌ها، {{domxref("TrustedHTML")}} را به روش‌ها ارسال کنید.

## پیکربندی‌های «مجاز»

می‌توانید یک [پیکربندی «مجاز» برای sanitizer](/en-US/docs/Web/API/HTML_Sanitizer_API#allow_and_remove_configurations) بسازید، فقط با مشخص کردن مجموعه‌ی عناصر و ویژگی‌هایی از HTML که می‌خواهید هنگام استفاده از sanitizer تزریق آن‌ها مجاز باشد. این نوع پیکربندی به‌راحتی قابل درک است و زمانی مفید است که دقیقاً بدانید چه موجودیت‌هایی باید در بافت هدف مجاز باشند.

برای مثال، پیکربندی زیر عناصر {{htmlelement("p")}} و {{htmlelement("div")}} و ویژگی‌های `cite` و `onclick` را «مجاز» می‌کند. همچنین عناصر {{htmlelement("b")}} را با محتوایشان جایگزین می‌کند (این نوعی «مجاز کردن» است، زیرا محتوای عنصر حذف نمی‌شود).

```js
const sanitizer = new Sanitizer({
  elements: ["p", "div"],
  attributes: ["cite", "onclick"],
  replaceWithChildrenElements: ["b"],
});
```

### مجاز کردن عناصر

عناصر مجاز را می‌توان با استفاده از ویژگی [`elements`](/en-US/docs/Web/API/SanitizerConfig#elements) از نمونه‌ی {{domxref("SanitizerConfig")}} که به سازنده‌ی `Sanitizer()` (یا مستقیماً به روش‌های پاکسازی) ارسال می‌شود، مشخص کرد.

ساده‌ترین راه برای استفاده از این ویژگی، تعیین یک آرایه از نام عناصر است:

```js
const sanitizer = new Sanitizer({
  elements: ["div", "span"],
});
```

اما همچنین می‌توانید هر یک از عناصر مجاز را با استفاده از یک شیء که `name` و `namespace` آن را تعریف می‌کند مشخص کنید، همان‌طور که در زیر نشان داده شده است (اگر `Sanitizer` بتواند، به‌طور خودکار namespace را استنباط می‌کند).

```js
const sanitizer = new Sanitizer({
  elements: [
    {
      name: "div",
      namespace: "http://www.w3.org/1999/xhtml",
    },
    {
      name: "span",
      namespace: "http://www.w3.org/1999/xhtml",
    },
  ],
});
```

همچنین می‌توانید عناصر را با استفاده از {{domxref("Sanitizer.allowElement()")}} به یک `Sanitizer` اضافه کنید. در اینجا ما همان عناصر را به یک sanitizer خالی اضافه می‌کنیم:

```js
const sanitizer = new Sanitizer({});
sanitizer.allowElement("div");
sanitizer.allowElement({
  name: "span",
  namespace: "http://www.w3.org/1999/xhtml",
});
```

### مجاز کردن ویژگی‌های سراسری

برای مجاز کردن ویژگی‌ها به‌صورت سراسری، روی هر عنصری که طبق مشخصات HTML مجاز باشد، می‌توانید از ویژگی [`attributes`](/en-US/docs/Web/API/SanitizerConfig#attributes_2) از {{domxref("SanitizerConfig")}} استفاده کنید.

ساده‌ترین راه برای استفاده از ویژگی `attributes` تعیین یک آرایه از نام ویژگی‌ها است:

```js
const sanitizer = new Sanitizer({
  attributes: ["cite", "onclick"],
});
```

همچنین می‌توانید هر ویژگی را با خصوصیات `name` و `namespace`، درست مانند عناصر، مشخص کنید:

```js
const sanitizer = new Sanitizer({
  attributes: [
    {
      name: "cite",
      namespace: null,
    },
    {
      name: "onclick",
      namespace: null,
    },
  ],
});
```

همچنین می‌توانید هر یک از ویژگی‌های مجاز را با استفاده از روش {{domxref("Sanitizer.allowAttribute()")}} به یک `Sanitizer` اضافه کنید:

```js
const sanitizer = new Sanitizer({});
sanitizer.allowAttribute("cite");
sanitizer.allowAttribute("onclick");
```

### مجاز کردن/حذف ویژگی‌ها روی یک عنصر خاص

همچنین می‌توانید ویژگی‌ها را در یک عنصر خاص مجاز کنید یا حذف کنید. توجه داشته باشید که این بخشی از یک «پیکربندی مجاز» است، زیرا در این حالت هنوز اجازه می‌دهید عنصر تزریق شود.

برای مجاز کردن یک ویژگی روی یک عنصر، می‌توانید عنصر را به‌صورت یک شیء با خصوصیات `name` و `attributes` مشخص کنید. ویژگی [`attributes`](/en-US/docs/Web/API/SanitizerConfig#attributes) شامل آرایه‌ای از ویژگی‌های مجاز روی آن عنصر است.

در زیر sanitizer نشان داده‌ایم که در آن عناصر {{htmlelement("div")}}، {{htmlelement("a")}} و {{htmlelement("span")}} مجاز هستند، و عنصر {{htmlelement("a")}} به‌طور اضافی ویژگی‌های `href`، `rel`، `hreflang` و `type` را مجاز می‌کند.

```js
const sanitizer = new Sanitizer({
  elements: [
    "div",
    { name: "a", attributes: ["href", "rel", "hreflang", "type"] },
    "span",
  ],
});
```

به‌طور مشابه، می‌توانیم ویژگی‌هایی را که در یک عنصر مجاز نیستند، با استفاده از یک شیء عنصر با ویژگی [`removeAttributes`](/en-US/docs/Web/API/SanitizerConfig#removeattributes) مشخص کنیم. برای مثال، sanitizer زیر ویژگی `type` را از همه‌ی عناصر `<a>` حذف می‌کند.

```js
const sanitizer = new Sanitizer({
  elements: ["div", { name: "a", removeAttributes: ["type"] }],
});
```

در هر دو حالت، می‌توانید هر ویژگی را به‌صورت یک شیء با خصوصیات `name` و `namespace` مشخص کنید. همچنین می‌توانید خصوصیات ویژگی‌ها را با استفاده از همان شیء عنصری که به {{domxref("Sanitizer.allowElement()")}} ارسال می‌شود، تنظیم کنید.

توجه داشته باشید که تعریف رفتار ویژگی به‌ازای هر عنصر روی یک `Sanitizer` با پیکربندی حذف (remove) غیرممکن است، زیرا آرایه‌ی (موردنیاز) `elements` وجود ندارد. سایر محدودیت‌های ویژگی‌های به‌ازای هر عنصر در [پیکربندی‌های معتبر](/en-US/docs/Web/API/SanitizerConfig#valid_configuration) پوشش داده شده‌اند.

### جایگزینی عناصر فرزند

می‌توانید آرایه‌ای از عناصر را مشخص کنید که با محتوای داخلی خود جایگزین شوند. این روش معمولاً برای حذف استایل‌ها از عناصر استفاده می‌شود.

برای مثال، کد زیر از ویژگی [`replaceWithChildrenElements`](/en-US/docs/Web/API/SanitizerConfig#replacewithchildrenelements) از {{domxref("SanitizerConfig")}} استفاده می‌کند تا مشخص کند عنصر {{htmlelement("b")}} باید جایگزین شود:

```js
const replaceBoldSanitizer = new Sanitizer({
  replaceWithChildrenElements: ["b"],
});

targetElement.setHTML("This <b>highlighting</b> isn't needed", {
  sanitizer: replaceBoldSanitizer,
});

// Log the result
console.log(targetElement.innerHTML); // This highlighting isn't needed
```

مانند عناصر و ویژگی‌ها، می‌توانید عناصر جایگزین را با namespace مشخص کنید، یا از روش {{domxref("Sanitizer.replaceElementWithChildren()")}} استفاده کنید:

```js
const sanitizer = new Sanitizer({});
sanitizer.replaceElementWithChildren("b");
sanitizer.replaceElementWithChildren({
  name: "i",
  namespace: "http://www.w3.org/1999/xhtml",
});
```

## پیکربندی‌های «حذف»

می‌توانید یک [پیکربندی «حذف» برای sanitizer](/en-US/docs/Web/API/HTML_Sanitizer_API#allow_and_remove_configurations) بسازید، با مشخص کردن مجموعه‌ی عناصر و ویژگی‌های HTML که می‌خواهید هنگام استفاده از sanitizer از ورودی حذف شوند. سایر عناصر و ویژگی‌ها توسط این پیکربندی مجاز هستند، اگرچه ممکن است اگر پیکربندی را در یک روش پاکسازی امن استفاده کنید حذف شوند.

> [!NOTE]
> یک پیکربندی sanitizer می‌تواند لیست‌های مجاز یا لیست‌های حذف را شامل شود، اما نه هر دو را.

برای مثال، پیکربندی زیر عناصر {{htmlelement("script")}}، {{htmlelement("div")}} و {{htmlelement("span")}} و همچنین ویژگی `onclick` را حذف می‌کند.

```js
const sanitizer = new Sanitizer({
  removeElements: ["script", "div", "span"],
  removeAttributes: ["onclick"],
});
```

مشخص کردن عناصری که باید حذف شوند، زمانی مفیدتر است که می‌خواهید یک پیکربندی موجود را تنظیم کنید. برای مثال، حالتی را در نظر بگیرید که از sanitizer پیش‌فرض (ایمن) استفاده می‌کنیم، اما می‌خواهیم مطمئن شویم برخی عناصر دیگر نیز حذف می‌شوند.

```js
const sanitizer = new Sanitizer();
sanitizer.removeElement("div");
```

### حذف عناصر

ویژگی [`removeElements`](/en-US/docs/Web/API/SanitizerConfig#removeelements) از یک نمونه‌ی {{domxref("SanitizerConfig")}} می‌تواند برای تعیین عناصری که باید حذف شوند استفاده شود.

ساده‌ترین راه برای استفاده از این ویژگی، تعیین یک آرایه از نام عناصر است:

```js
const sanitizer = new Sanitizer({
  removeElements: ["div", "span"],
});
```

همان‌طور که در [مجاز کردن عنصر](#allowing_elements) می‌توانید هر یک از عناصر مورد حذف را با استفاده از یک شیء که `name` و `namespace` آن را تعریف می‌کند مشخص کنید. همچنین می‌توانید عناصر حذف‌شده را با استفاده از API `Sanitizer` همان‌طور که نشان داده شده پیکربندی کنید:

```js
const sanitizer = new Sanitizer({});
sanitizer.removeElement("div");
sanitizer.removeElement({
  name: "span",
  namespace: "http://www.w3.org/1999/xhtml",
});
```

### ح