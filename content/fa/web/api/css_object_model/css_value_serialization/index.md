---
title: "CSS value serialization"
---

---
title: CSS value serialization
slug: Web/API/CSS_Object_Model/CSS_value_serialization
page-type: guide
spec-urls:
  - https://drafts.csswg.org/cssom/#serialize-a-css-value
  - https://drafts.csswg.org/css-color-4/#serialization
---

{{APIRef("CSSOM")}}

برخی از APIهای CSSOM، مقادیر ویژگی‌ها را بر اساس [نوع داده](/en-US/docs/Web/CSS/Reference/Values/Data_types)یِ آن مقدار، به نمایش‌های رشته‌ای استانداردی _سریال‌سازی_ می‌کنند. برای مثال، ممکن است یک رنگ را با استفاده از نحو `hsl(240 100% 50%)` تنظیم کنید، اما وقتی از طریق جاوااسکریپت به آن دسترسی پیدا کنید، مقدار معادل به شکل `"rgb(0, 0, 255)"` بازگردانده می‌شود.

انواع داده‌ی CSS اغلب می‌توانند با چندین نحو بیان شوند. برای مثال، نوع داده‌ی {{cssxref("&lt;color&gt;")}} را می‌توان با رنگ‌های نام‌گذاری‌شده (`red`)، نماد هگزادسیمال (`#ff0000`)، نماد تابعی (`rgb(255 0 0)`) و موارد دیگر نمایش داد. این نحوهای مختلف در تمام مراحل [پردازش مقدار CSS](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing) دقیقاً معادل یکدیگرند؛ مشابه اینکه در جاوااسکریپت، یک رشته‌ی یکسان را می‌توان با نقل‌قول تکی یا دوتایی نوشت، یا یک عدد یکسان را در قالب‌های متفاوتی (مانند `16`، `16.0` یا `0x10`) نوشت.

از آنجا که CSS در طول پردازش مقدار، همه‌ی این نمایش‌های سطحی را به مقدار زیربناییِ یکسانی تبدیل می‌کند، بازیابی نحو اصلی از CSSOMِ تجزیه‌شده اغلب غیرممکن است. علاوه بر این، یک نمایش _متعارف_ (canonical) معمولاً برای اسکریپت‌ها کاربرد بیشتری دارد، زیرا امکان مقایسه و محاسبه را بر اساس نحوه‌ی ارائه‌ی محتوا به کاربر فراهم می‌کند، نه بر اساس روشی که در ابتدا نگارش شده است.

## چه زمانی و چگونه مقادیر سریال‌سازی می‌شوند

سریال‌سازی زمانی رخ می‌دهد که مقادیر ویژگی‌های CSS از طریق APIهای جاوااسکریپت به صورت رشته خوانده شوند، مانند:

- {{domxref("CSSStyleDeclaration.getPropertyValue()")}}
- {{domxref("CSSStyleDeclaration.cssText")}}
- دسترسی مستقیم به ویژگی‌ها روی آبجکت‌های {{domxref("CSSStyleDeclaration")}} (مثلاً `element.style.backgroundColor`)

APIهای مختلف، آبجکت‌های `CSSStyleDeclaration` را در مراحل متفاوتی از [پردازش مقدار](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing) بازمی‌گردانند که رفتارهای سریال‌سازیِ کمی متفاوتی دارند. برای مثال، {{domxref("Window.getComputedStyle()")}} و {{domxref("HTMLElement.style")}} [مقدار حل‌شده](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#resolved_value) ویژگی‌ها را بازمی‌گردانند، در حالی که {{domxref("CSSStyleRule.style")}} _کمابیش_ [مقدار اعلام‌شده](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#declared_value) را بازمی‌گرداند.

> [!NOTE]
> [CSS Typed OM API](/en-US/docs/Web/API/CSS_Typed_OM_API) قادر است واحدها و سایر نحوهای CSS را نمایش دهد؛ با این حال، اعلان‌های استایلی که از یک عنصر بازیابی می‌شوند همچنان پردازش می‌شوند و نحو اصلی را حفظ نمی‌کنند. برای مثال، `CSS.cm(1).toString()` به جای سریال‌سازی به پیکسل، `"1cm"` را برمی‌گرداند، اما `element.computedStyleMap().get("margin-left").toString()` مقدار پیکسلیِ حل‌شده را برمی‌گرداند.

هر نوع مقدار CSS دارای قالب سریال‌سازیِ مرتبطی است که توسط مشخصات CSS تعریف شده است. برخی از قواعد رایج عبارت‌اند از:

- کلیدواژه‌ها (مانند `auto`، `block`، `none`) به صورت تمام‌حروف کوچک سریال‌سازی می‌شوند.
- {{cssxref("angle")}}: بسته به زمینه، به یک واحد زاویه سریال‌سازی می‌شود (نامشخص). برای `element.style` و `getComputedStyle()`، این واحد `deg` است.
- {{cssxref("&lt;color&gt;")}}:
  - برای رنگ‌های sRGB ({{cssxref("named-color")}}، `transparent`، {{cssxref("system-color")}}، {{cssxref("hex-color")}}، `rgb`، `hsl`، `hwb`): به صورت نحو قدیمیِ جداشده با کاما `rgb(R, G, B)` یا `rgba(R, G, B, A)` سریال‌سازی می‌شود، که در آن همه‌ی آرگومان‌ها عدد هستند. اگر آلفا دقیقاً `1` باشد، شکل `rgb` انتخاب می‌شود.
  - برای رنگ‌های `lab()`، `lch()`، `oklab()`، `oklch()` و `color()`: شکل تابعی با آرگومان‌های عددی حفظ می‌شود.
  - کلیدواژه‌ی `currentColor` به صورت `currentcolor` سریال‌سازی می‌شود.
- {{cssxref("percentage")}}: به صورت درصد حفظ می‌شود.
- {{cssxref("ratio")}}: به صورت دو عدد که با `" / "` از هم جدا شده‌اند سریال‌سازی می‌شود.
- {{cssxref("url_value", "&lt;url&gt;")}}: به صورت یک {{cssxref("url_value", "&lt;url&gt;")}} با نقل‌قول (`url("...")`) سریال‌سازی می‌شود و URL به یک URL مطلق تبدیل می‌شود.

توجه داشته باشید که مقادیر `<percentage>` در طول پردازش مقدار اغلب به ابعاد مطلق (مانند `<length>`) تبدیل می‌شوند، بنابراین هنگام سریال‌سازی از استایل‌های محاسبه‌شده ممکن است به صورت درصد ظاهر نشوند. برای ابعادی که واحد دارند، مانند {{cssxref("&lt;frequency&gt;")}}، {{cssxref("&lt;length&gt;")}}، {{cssxref("&lt;resolution&gt;")}} و {{cssxref("&lt;time&gt;")}}، واحد سریال‌سازی‌شده به زمینه بستگی دارد و به خوبی مشخص نشده است. `getComputedStyle()` و `element.style` آن‌ها را به ترتیب به `Hz`، `px`، `dppx` و `s` سریال‌سازی می‌کنند.

هنگام سریال‌سازی مقدار ویژگی‌های کوتاه‌نویسی (shorthand)، ویژگی‌های بلندنویسی (longhand)ِ تشکیل‌دهنده‌ی آن بر اساس قواعد مربوط به آن ویژگی کوتاه‌نویسی سریال‌سازی و ترکیب می‌شوند.

> [!NOTE]
> جزئیات پیچیده‌ی زیادی درباره‌ی نحوه‌ی سریال‌سازی ویژگی‌های CSS وجود دارد، به‌ویژه برای ویژگی‌های پیچیده‌ای مانند `font`. این جزئیات ممکن است در مشخصات تعریف نشده باشند یا حتی در مرورگرهای مختلف ناسازگار باشند. برای مورد استفاده‌ی خاص خودتان باید رفتار را آزمایش و تأیید کنید.

```html
<div>Example Element</div>
```

```css
div {
  position: absolute; /* keyword */
  rotate: 1rad; /* <angle> */
  color: hsl(240 100% 50%); /* <color> */
  background-color: hsl(120 50% 50% / 0.3); /* <color> with alpha */
  border-color: lab(10 -120 -120); /* <color> in non-sRGB space */
  margin: 2em; /* relative <length> */
  padding: 2cm; /* absolute <length> */
  font-size: calc(1em + 2px); /* complex expression */
  left: 50%; /* <percentage> */
  animation-duration: 500ms; /* <time> */
}
```

```js
const element = document.querySelector("div");
const table = document.createElement("table");
const elemStyle = getComputedStyle(element);
const ruleStyle = document.getElementById("css-output").sheet.cssRules[0].style;
const head = table.createTHead().insertRow();
["Property", "getComputedStyle()", "CSSStyleRule"].forEach((text) => {
  const th = document.createElement("th");
  th.textContent = text;
  head.appendChild(th);
});
for (const property of [
  "position",
  "rotate",
  "color",
  "background-color",
  "border-color",
  "margin",
  "padding",
  "font-size",
  "left",
  "animation-duration",
]) {
  const row = document.createElement("tr");
  const propCell = document.createElement("td");
  const valueCell = document.createElement("td");
  const ruleCell = document.createElement("td");
  propCell.textContent = property;
  valueCell.textContent = elemStyle.getPropertyValue(property);
  ruleCell.textContent = ruleStyle.getPropertyValue(property);
  row.appendChild(propCell);
  row.appendChild(valueCell);
  row.appendChild(ruleCell);
  table.appendChild(row);
}
document.body.appendChild(table);
```

{{EmbedLiveSample("", "", 400)}}

## مثال‌ها

### سریال‌سازی مقدار رنگ

رنگ‌ها از رایج‌ترین انواعی هستند که از سریال‌سازی تأثیر می‌پذیرند. صرف‌نظر از اینکه یک رنگ را با `hsl()`، `hwb()`، یک کلیدواژه یا یک فضای رنگی مدرن تعریف کنید، جاوااسکریپت معمولاً آن را در [قالب قدیمی `rgb()` یا `rgba()`](/en-US/docs/Web/CSS/Reference/Values/color_value/rgb#syntax) برمی‌گرداند.

مثال‌های زیر نشان می‌دهند که چگونه قالب‌های رنگی مختلف هنگام دسترسی از طریق جاوااسکریپت سریال‌سازی می‌شوند.

```html
<div class="example hsl">HSL Color</div>
<div class="example lab">LAB Color</div>
<div class="example named">Named Color</div>
<div class="example alpha">Transparent Color</div>
<pre id="output"></pre>
```

```css
.example {
  padding: 10px;
  margin: 5px;
  color: white;
}

.hsl {
  background-color: hsl(240 100% 50%);
}

.lab {
  background-color: lab(100% 0 0);
}

.named {
  background-color: blue;
}

.alpha {
  background-color: hsl(120 50% 50% / 0.3);
}
```

```js
const examples = document.querySelectorAll(".example");
const output = document.getElementById("output");

examples.forEach((element) => {
  const style = getComputedStyle(element);
  output.textContent += `${element.className}: ${style.getPropertyValue("background-color")}\n`;
});
```

{{EmbedLiveSample("Color value serialization", , 400)}}

### سریال‌سازی مقدار طول

طول‌ها نیز مورد رایج دیگری هستند. واحدهای نسبی (مانند `em`، `%`) اغلب هنگام سریال‌سازی از طریق APIهای جاوااسکریپت به پیکسل‌های مطلق تبدیل می‌شوند.

```js
element.style.marginLeft = "2em";
console.log(getComputedStyle(element).marginLeft);
// "32px" (depending on font size)
```

این نرمال‌سازی به اسکریپت‌ها امکان می‌دهد طول‌ها را به شکلی سازگار مقایسه یا محاسبه کنند.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`CSSStyleDeclaration.getPropertyValue()`](/en-US/docs/Web/API/CSSStyleDeclaration/getPropertyValue)
- [`Window.getComputedStyle()`](/en-US/docs/Web/API/Window/getComputedStyle)
- [رنگ‌های CSS](/en-US/docs/Web/CSS/Guides/Colors)
- {{cssxref("&lt;color&gt;")}}
- ماژول [مقادیر و واحدهای CSS](/en-US/docs/Web/CSS/Guides/Values_and_units)