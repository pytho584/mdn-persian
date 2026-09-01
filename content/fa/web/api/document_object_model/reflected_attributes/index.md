---
title: "Attribute reflection"
---

---
title: Attribute reflection
slug: Web/API/Document_Object_Model/Reflected_attributes
page-type: guide
---

{{DefaultAPISidebar("DOM")}}

یک {{glossary("attribute", "ویژگی")}} یک {{glossary("HTML")}}، {{glossary("XML")}}، {{glossary("SVG")}} یا {{glossary("element", "عنصر")}} دیگر را گسترش می‌دهد، رفتار آن را تغییر می‌دهد یا فراداده ارائه می‌کند.

بسیاری از ویژگی‌ها در رابط {{glossary("DOM")}} متناظر _بازتابیده_ می‌شوند.
این بدان معناست که مقدار ویژگی را می‌توان مستقیماً در جاوااسکریپت از طریق یک ویژگی (property) روی رابط متناظر خواند یا نوشت، و بالعکس.
ویژگی‌های بازتابیده رویکرد برنامه‌نویسی طبیعی‌تری نسبت به دریافت و تنظیم مقادیر ویژگی با استفاده از روش‌های {{domxref("Element.getAttribute()","getAttribute()")}} و {{domxref("Element.setAttribute()","setAttribute()")}} رابط {{domxref("Element")}} ارائه می‌دهند.

این راهنما مروری بر ویژگی‌های بازتابیده و نحوه استفاده از آنها ارائه می‌دهد.

## دریافت‌کننده/تنظیم‌کننده ویژگی

ابتدا مکانیسم پیش‌فرض برای دریافت و تنظیم یک ویژگی را بررسی می‌کنیم، که می‌تواند بدون توجه به بازتابیده بودن یا نبودن ویژگی استفاده شود.
برای دریافت ویژگی، متد {{domxref("Element.getAttribute()","getAttribute()")}} رابط {{domxref("Element")}} را با مشخص کردن نام ویژگی فراخوانی می‌کنید.
برای تنظیم ویژگی، متد {{domxref("Element.setAttribute()","setAttribute()")}} را با مشخص کردن نام ویژگی و مقدار جدید فراخوانی می‌کنید.

HTML زیر را در نظر بگیرید:

```html
<input placeholder="متن پیش‌فرض" />
```

برای دریافت و تنظیم ویژگی [`placeholder`](/en-US/docs/Web/HTML/Reference/Attributes/placeholder):

```js
const input = document.querySelector("input");

// دریافت ویژگی placeholder
let attr = input.getAttribute("placeholder");

// تنظیم ویژگی placeholder
input.setAttribute("placeholder", "متن تغییر یافته");
```

## ویژگی‌های بازتابیده

برای یک {{htmlelement("input")}}، ویژگی `placeholder` توسط ویژگی {{domxref("HTMLInputElement.placeholder")}} بازتابیده می‌شود.
با همان HTML قبلی:

```html
<input placeholder="متن پیش‌فرض" />
```

همان عملیات را می‌توان به طور طبیعی‌تری با استفاده از ویژگی `placeholder` انجام داد:

```js
const input = document.querySelector("input");

// دریافت ویژگی placeholder
let attr = input.placeholder;

// تنظیم ویژگی placeholder
input.placeholder = "متن تغییر یافته";
```

توجه کنید که نام ویژگی بازتابیده و ویژگی (property) یکسان است: `placeholder`.
همیشه اینطور نیست: ویژگی‌ها معمولاً با پیروی از قرارداد {{glossary("Camel case","camelCase")}} نام‌گذاری می‌شوند.
این موضوع به ویژه برای نام ویژگی‌های چندکلمه‌ای که حاوی کاراکترهایی هستند که در نام ویژگی‌های جاوااسکریپت مجاز نیستند، مانند خط تیره، صادق است.
برای مثال، ویژگی [aria-checked](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked) توسط ویژگی [`ariaChecked`](/en-US/docs/Web/API/Element/ariaChecked) بازتابیده می‌شود.

### ویژگی‌های بازتابیده بولی

{{Glossary("Boolean/HTML", "ویژگی‌های بولی")}} کمی متفاوت از دیگران هستند زیرا نیازی به اعلام با نام و مقدار ندارند.
برای مثال، عنصر checkbox {{htmlelement("input")}} زیر دارای ویژگی `checked` است و در نمایش علامت‌خورده خواهد بود:

```html
<input type="checkbox" checked />
```

متد {{domxref("Element.getAttribute()")}} در صورت علامت‌خورده بودن ورودی رشته‌ی خالی `""` و در غیر این صورت `null` برمی‌گرداند.
ویژگی متناظر {{domxref("HTMLInputElement.checked")}} برای وضعیت علامت‌خورده `true` یا `false` برمی‌گرداند.
در غیر این صورت، ویژگی‌های بازتابیده بولی مانند سایر ویژگی‌های بازتابیده هستند.

### ویژگی‌های بازتابیده شمارشی

در HTML، [ویژگی‌های شمارشی](https://html.spec.whatwg.org/multipage/common-microsyntaxes.html#enumerated-attribute) ویژگی‌هایی با مجموعه محدود و از پیش تعریف‌شده‌ای از مقادیر متنی هستند. برای مثال، ویژگی سراسری HTML [`dir`](/en-US/docs/Web/HTML/Reference/Global_attributes/dir) سه مقدار معتبر دارد: `ltr`، `rtl` و `auto`.

```html
<p dir="rtl">راست به چپ</p>
```

مانند نام تگ‌های HTML، ویژگی‌های شمارشی HTML و مقادیر آنها به حروف بزرگ و کوچک حساس نیستند، بنابراین `LTR`، `RTL` و `AUTO` نیز کار می‌کنند.

```html
<p dir="RTL">راست به چپ</p>
```

ویژگی بازتابیده IDL، {{domxref("HTMLElement.dir")}}، همیشه یک مقدار متعارف (canonical) را مطابق مشخصات (در این مثال مقادیر با حروف کوچک) برمی‌گرداند. تنظیم مقدار نیز آن را به شکل متعارف سریال‌سازی می‌کند.

```js
const pElement = document.querySelector("p");
console.log(pElement.dir); // "rtl"
pElement.dir = "RTL";
console.log(pElement.dir); // "rtl"
```

به طور جایگزین، می‌توانید از متد {{domxref("Element.getAttribute()","getAttribute()")}} رابط {{domxref("Element")}} استفاده کنید. این متد مقدار ویژگی را بدون تغییر از HTML دریافت می‌کند.

```js
const pElement = document.querySelector("p");
console.log(pElement.getAttribute("dir")); // "RTL"
```

## ارجاع‌های عنصر بازتابیده

> [!NOTE]
> این بخش در مورد [ویژگی‌های ARIA بازتابیده که حاوی ارجاع به عناصر هستند](/en-US/docs/Web/API/Element#instance_properties_reflected_from_aria_element_references) اعمال می‌شود.
> ملاحظات مشابه احتمالاً برای سایر/ویژگی‌های آینده که ارجاع به عناصر را بازتاب می‌دهند نیز صادق است.

برخی ویژگی‌ها ارجاع به _عناصر_ را به عنوان مقدار می‌پذیرند: یا یک مقدار `id` عنصر یا یک رشته از مقادیر `id` عنصر که با فاصله جدا شده‌اند.
این مقادیر `id` به عناصر دیگری اشاره می‌کنند که با ویژگی مرتبط هستند، یا حاوی اطلاعاتی هستند که ویژگی به آنها نیاز دارد.
این ویژگی‌ها توسط یک ویژگی متناظر به عنوان یک آرایه از نمونه‌های شیء مشتق‌شده از {{domxref("HTMLElement")}} که با مقادیر `id` مطابقت دارند، بازتابیده می‌شوند، با برخی ملاحظات.

برای مثال، ویژگی [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) مقادیر `id` عناصری را فهرست می‌کند که نام دسترس‌پذیر (accessible name) یک عنصر را در متن داخلی خود دارند.
HTML زیر این را برای یک {{htmlelement("input")}} نشان می‌دهد که دارای برچسبی تعریف‌شده در عناصر {{htmlelement("span")}} با مقادیر `id` برابر با `label_1`، `label_2` و `label_3` است:

```html
<span id="label_1">(متن برچسب ۱)</span>
<span id="label_2">(متن برچسب ۲)</span>
<input aria-labelledby="label_1 label_2 label_3" />
```

این ویژگی توسط ویژگی {{domxref("Element.ariaLabelledByElements")}} بازتابیده می‌شود که آرایه‌ای از عناصر دارای مقادیر `id` متناظر را برمی‌گرداند.
ویژگی و ویژگی متناظر را می‌توان به صورت زیر برگرداند:

```js
const inputElement = document.querySelector("input");

console.log(inputElement.getAttribute("aria-labelledby"));
// "label_1 label_2 label_3"

console.log(inputElement.ariaLabelledByElements);
// [HTMLSpanElement, HTMLSpanElement]
```

نکته اول از کد بالا این است که ویژگی و ویژگی (property) تعداد متفاوتی از عناصر را شامل می‌شوند — ویژگی مستقیماً ویژگی را بازتاب نمی‌دهد زیرا ارجاع `label_3` عنصر متناظری ندارد.
همچنین ممکن است یک ارجاع مطابقت نداشته باشد زیرا `id` [خارج از محدوده عنصر](#element_id_reference_scope) است.
این می‌تواند زمانی اتفاق بیفتد که عنصر ارجاع‌شده در همان DOM یا shadow DOM عنصر نباشد، زیرا شناسه‌ها فقط در محدوده‌ای که اعلام شده‌اند معتبر هستند.

ما می‌توانیم عناصر موجود در آرایه ویژگی را پیمایش کنیم، در این مورد برای دریافت نام دسترس‌پذیر از متن داخلی آنها (این کار طبیعی‌تر از استفاده از ویژگی است، زیرا نیازی به دریافت اولیه ارجاع‌های عنصر و سپس استفاده از آنها برای یافتن عناصر نداریم، و فقط باید با عناصری کار کنیم که می‌دانیم در محدوده فعلی در دسترس هستند):

```js
const inputElement = document.querySelector("input");
const accessibleName = inputElement.ariaLabelledByElements
  .map((e) => e.textContent.trim())
  .join(" ");
console.log(accessibleName);
// (متن برچسب ۱) (متن برچسب ۲)
```

### تنظیم ویژگی و ویژگی (property)

برای ویژگی‌های بازتابیده معمولی، به‌روزرسانی‌های ویژگی (property) در ویژگی متناظر منعکس می‌شوند و بالعکس.
برای ارجاع‌های عنصر بازتابیده اینطور نیست.
در عوض، تنظیم ویژگی (property) ویژگی (attribute) را پاک می‌کند (تنظیم مجدد)، به طوری که ویژگی و ویژگی دیگر یکدیگر را بازتاب نمی‌دهند.
برای مثال، با HTML زیر:

```html
<span id="label_1">(متن برچسب ۱)</span>
<span id="label_2">(متن برچسب ۲)</span>
<input aria-labelledby="label_1 label_2" />
```

مقدار اولیه `aria-labelledby` برابر با `"label_1 label_2"` است، اما اگر آن را از DOM API تنظیم کنیم، ویژگی به `""` بازنشانی می‌شود:

```js
const inputElement = document.querySelector("input");

let attributeValue = inputElement.getAttribute("aria-labelledby");
console.log(attributeValue);
// "label_1 label_2"

// تنظیم ویژگی با استفاده از ویژگی بازتابیده
inputElement.ariaLabelledByElements = document.querySelectorAll("span");

attributeValue = inputElement.getAttribute("aria-labelledby");
console.log(attributeValue);
// ""
```

این منطقی است زیرا در غیر این صورت می‌توانستید عناصری را به ویژگی اختصاص دهید که ارجاع `id` ندارند، و بنابراین نمی‌توانند در ویژگی نمایش داده شوند.

تنظیم مقدار ویژگی، رابطه بین ویژگی و ویژگی (property) را بازمی‌گرداند.
ادامه مثال بالا:

```js
inputElement.setAttribute("aria-labelledby", "label_1");

attributeValue = inputElement.getAttribute("aria-labelledby");
console.log(attributeValue);
// "label_1"

// تنظیم ویژگی با استفاده از ویژگی بازتابیده
console.log(inputElement.ariaLabelledByElements);
// [HTMLSpanElement] - برای `label_1`
```

آرایه برگردانده شده توسط ویژگی (property) ایستا است، بنابراین نمی‌توانید آرایه برگردانده شده را تغییر دهید تا باعث تغییرات در ویژگی متناظر شوید.
هنگامی که یک آرایه به ویژگی اختصاص داده می‌شود، کپی می‌شود، بنابراین هر تغییری در ویژگی در آرایه ویژگی که قبلاً برگردانده شده منعکس نخواهد شد.

### محدوده ارجاع شناسه عنصر

ارجاع‌های ویژگی عنصر فقط می‌توانند به عناصر دیگری که در همان DOM یا [Shadow DOM](/en-US/docs/Web/API/Web_components#shadow_dom_2) هستند اشاره کنند، زیرا شناسه‌های عنصر فقط در محدوده‌ای که اعلام شده‌اند معتبر هستند.

ما می‌توانیم این را در کد زیر ببینیم.
ویژگی [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) عنصر {{htmlelement("input")}} به عناصر با شناسه‌های `label_1`، `label_2` و `label_3` ارجاع می‌دهد.
با این حال `label_3` در این مورد یک شناسه معتبر نیست زیرا در همان محدوده عنصر {{htmlelement("input")}} تعریف نشده است.
در نتیجه، برچسب فقط از عناصر با شناسه‌های `label_1` و `label_2` خواهد آمد.

```html
<div id="in_dom">
  <span id="label_3">(متن برچسب ۳)</span>
</div>
<div id="host">
  <template shadowrootmode="open">
    <span id="label_1">(متن برچسب ۱)</span>
    <input aria-labelledby="label_1 label_2 label_3" />
    <span id="label_2">(متن برچسب ۲)</span>
  </template>
</div>
```

### محدوده ارجاع عنصر بازتابیده

هنگام استفاده از [ویژگی‌های نمونه بازتابیده از ارجاع‌های عنصر ARIA](/en-US/docs/Web/API/Element#instance_properties_reflected_from_aria_element_references)، مانند {{domxref("Element.ariaLabelledByElements")}} برای `aria-labelledby`، قوانین محدوده کمی متفاوت است.
برای اینکه در محدوده باشد، یک عنصر هدف باید در همان DOM عنصر ارجاع‌دهنده، یا یک DOM والد باشد.
عناصر در DOMهای دیگر، از جمله shadow DOMهایی که فرزند یا هم‌سطح DOM ارجاع‌دهنده هستند، خارج از محدوده هستند.

مثال زیر حالتی را نشان می‌دهد که یک عنصر در DOM والد (`label_3`) به عنوان هدف تنظیم می‌شود، همراه با عناصر با شناسه‌های `label_1` و `label_2` که در همان ریشه shadow اعلام شده‌اند.
این کار می‌کند زیرا همه عناصر هدف برای عنصر ارجاع‌دهنده در محدوده هستند.

```html
<div id="in_dom">
  <span id="label_3">(متن برچسب ۳)</span>
</div>
<div id="host">
  <template shadowrootmode="open">
    <span id="label_1">(متن برچسب ۱)</span>
    <input id="input" />
    <span id="label_2">(متن برچسب ۲)</span>
  </template>
</div>
```

```js
const host = document.getElementById("host");
const input = host.shadowRoot.getElementById("input");
input.ariaLabelledByElements = [
  host.shadowRoot.getElementById("label_1"),
  host.shadowRoot.getElementById("label_2"),
  document.getElementById("label_3"),
];
```

کد معادل با یک عنصر در DOM که به عنصری در shadow DOM ارجاع می‌دهد کار نخواهد کرد، زیرا عناصر هدفی که در shadow DOMهای تو در تو هستند در محدوده نیستند:

```html
<div id="in_dom">
  <span id="label_1">(متن برچسب ۱)</span>
  <input id="input" />
  <span id="label_2">(متن برچسب ۲)</span>
</div>
<div id="host">
  <template shadowrootmode="open">
    <span id="label_3">(متن برچسب ۳)</span>
  </template>
</div>
```

```js
const host = document.getElementById("host");
const input = document.getElementById("input");
input.ariaLabelledByElements = [
  host.shadowRoot.getElementById("label_3"),
  document.getElementById("label_1"),
  document.getElementById("label_2"),
];
```

توجه کنید که یک عنصر ممکن است در ابتدا "در محدوده" باشد و سپس به خارج از محدوده به یک ریشه shadow تو در تو منتقل شود.
در این مورد، عنصر ارجاع‌شده همچنان در ویژگی فهرست می‌شود، اما در ویژگی (property) برگردانده نمی‌شود.
با این حال توجه داشته باشید که اگر عنصر به محدوده بازگردانده شود، دوباره در ویژگی بازتابیده حضور خواهد داشت.

### خلاصه رابطه ویژگی/ویژگی (property)

رابطه بین ویژگی‌های حاوی ارجاع به عناصر و ویژگی متناظر آنها به شرح زیر است:

- ارجاع‌های `id` عنصر ویژگی فقط برای عناصر هدفی که در همان DOM یا shadow DOM عنصر اعلام شده‌اند [در محدوده](#element_id_reference_scope) هستند.
- ویژگی‌هایی که ارجاع‌های عنصر ARIA را بازتاب می‌دهند می‌توانند عناصر را در همان محدوده یا یک محدوده والد هدف قرار دهند. عناصر در محدوده‌های تو در تو قابل دسترسی نیستند.
- تنظیم ویژگی (property) ویژگی (attribute) را پاک می‌کند و ویژگی و ویژگی دیگر یکدیگر را بازتاب نمی‌دهند.
  اگر ویژگی با {{domxref("Element.getAttribute()")}} خوانده شود، مقدار `""` است.
- تنظیم ویژگی (attribute) با {{domxref("Element.setAttribute()")}} همچنین ویژگی (property) را تنظیم می‌کند و "رابطه بازتاب" را بازمی‌گرداند.
- تنظیم ویژگی با یک مقدار ارجاع که متعاقباً از محدوده خارج می‌شود منجر به حذف عنصر متناظر از آرایه ویژگی می‌شود.
  با این حال توجه داشته باشید که ویژگی همچنان حاوی ارجاع است، و اگر عنصر به محدوده بازگردانده شود، ویژگی دوباره عنصر را شامل می‌شود (یعنی رابطه بازسازی می‌شود).