---
title: Using dynamic styling information
slug: Web/API/CSS_Object_Model/Using_dynamic_styling_information
page-type: guide
---

{{DefaultAPISidebar("CSSOM")}}

مدل شیءِ CSS (CSSOM) که بخشی از DOM است، رابط‌های مشخصی را در معرض دید قرار می‌دهد که امکان دستکاری حجم گسترده‌ای از اطلاعات مربوط به CSS را فراهم می‌کنند. این رابط‌ها ابتدا در توصیه‌نامهٔ _DOM Level 2 Style_ تعریف شده بودند و اکنون یک مشخصات به نام _CSS Object Model (CSSOM)_ تشکیل می‌دهند که هدف آن جایگزین کردن آن توصیه‌نامه است.

در بسیاری از موارد، و تا جایی که ممکن باشد، بهترین روش آن است که کلاس‌ها را به‌صورت پویا از طریق ویژگی {{ domxref("element.className", "className") }} تغییر دهید؛ زیرا می‌توان ظاهر نهایی همهٔ قلاب‌های استایل را در یک شیوه‌نامه (stylesheet) واحد کنترل کرد. به این ترتیب کد جاوااسکریپت شما نیز تمیزتر می‌شود؛ به‌جای آن‌که درگیر جزئیات استایل‌بندی شود، می‌تواند بر معنای کلی هر بخشی که می‌سازد یا تغییر می‌دهد تمرکز کند و جزئیات دقیق ظاهری را به شیوه‌نامه بسپارد. با این حال، مواردی وجود دارد که به‌دست آوردن یا دستکاری خودِ قواعد می‌تواند مفید باشد (چه برای کل شیوه‌نامه‌ها و چه برای عناصر تکی)؛ این موارد در ادامه با جزئیات بیشتری شرح داده شده‌اند. همچنین توجه داشته باشید که همان‌طور که در مورد استایل‌های DOM مربوط به یک عنصر وجود دارد، وقتی از دستکاری شیوه‌نامه‌ها صحبت می‌کنیم، مقصود دستکاریِ سند فیزیکی نیست، بلکه صرفاً تغییر نمایش داخلی سند است.

شیء پایهٔ `style` رابط‌های {{domxref("Stylesheet")}} و {{domxref("CSSStylesheet")}} را در معرض دید قرار می‌دهد. این رابط‌ها اعضایی مانند `insertRule`، `selectorText` و `parentStyleSheet` دارند که برای دسترسی به قواعد استایل تکیِ تشکیل‌دهندهٔ یک شیوه‌نامهٔ CSS و دستکاری آن‌ها به کار می‌روند.

برای دسترسی به اشیاء `style` از روی `document`، می‌توانید از ویژگی {{domxref("Document.styleSheets")}} استفاده کنید و اشیاء تکی را با فهرست (index) مورد دسترسی قرار دهید (مثلاً `document.styleSheets[0]` اولین شیوه‌نامهٔ تعریف‌شده برای سند است، و به همین ترتیب). همچنین می‌توانید ویژگی {{domxref("HTMLStyleElement.sheet", "sheet")}} را روی یک عنصر `<style>` خاص صدا بزنید تا شیء شیوه‌نامهٔ مرتبط با آن را دریافت کنید.

## تغییر یک قاعدهٔ شیوه‌نامه با CSSOM

در این مثال، پس‌زمینهٔ صفحه با استفاده از CSS به رنگ `red` تنظیم شده است. سپس جاوااسکریپت با استفاده از CSSOM به این ویژگی دسترسی پیدا می‌کند و رنگ پس‌زمینه را به `cornflowerblue` تغییر می‌دهد.

```html live-sample___modify-rule
<p>The stylesheet declaration for the body is modified via JavaScript.</p>
```

```css live-sample___modify-rule
body {
  background-color: red;
  font: 1.2em / 1.5 sans-serif;
  color: white;
  padding: 1em;
}
```

```js live-sample___modify-rule
const stylesheet = document.getElementById("css-output").sheet;
stylesheet.cssRules[0].style.backgroundColor = "cornflowerblue";
```

{{EmbedLiveSample("modify-rule")}}

فهرست ویژگی‌های موجود در DOM از طریق ویژگی `style` در صفحهٔ [فهرست ویژگی‌های CSS در DOM](/en-US/docs/Web/CSS/Reference) آمده است.

برای تغییر استایل‌های یک سند با استفاده از نحو CSS، می‌توانید قاعده‌هایی را درج کنید یا تگ‌های {{HTMLElement("style")}} را اضافه کنید که ویژگی `innerHTML` آن‌ها روی CSS موردنظر تنظیم شده است.

## تغییر استایل یک عنصر

ویژگی `style` عنصر (همچنین به بخش «شیء استایل DOM» در زیر مراجعه کنید) می‌تواند برای دریافت و تنظیم استایل‌های یک عنصر به کار رود. با این حال، این ویژگی فقط آن دسته از ویژگی‌های استایلی را برمی‌گرداند که به‌صورت _درونخطی_ تنظیم شده باشند (مثلاً دسترسی به `element.style.color` روی عنصری که به‌صورت `<td style="background-color: lightblue">` تعریف شده است، رشتهٔ `""` را برمی‌گرداند، حتی اگر ممکن است آن عنصر دارای `color` تعریف‌شده از طریق یک شیوه‌نامه باشد).

علاوه بر این، وقتی این ویژگی را روی یک عنصر تنظیم می‌کنید، هر استایلی را که برای همان ویژگی خاص این عنصر جای دیگری تعیین شده باشد، بازنویسی (override) می‌کنید. برای مثال، تنظیم ویژگی `border`، تنظیماتی را که برای ویژگی `border` این عنصر در بخش head یا در شیوه‌نامه‌های خارجی انجام شده است بازنویسی می‌کند. با این حال، این کار هیچ تأثیری بر سایر اعلان‌های ویژگیِ مربوط به استایل این عنصر ندارد؛ برای مثال بر `padding`، `margin` یا `font`.

برای تغییر استایل یک عنصر خاص، می‌توانید مثال زیر را برای عنصر(هایی) که می‌خواهید استایل‌بندی کنید، تطبیق دهید.

```html
<p id="p1">Click here to change background color.</p>
<button>Reset background color</button>
```

```css
#p1 {
  border: solid blue 2px;
}
```

```js
const p1 = document.getElementById("p1");
const button = document.querySelector("button");

p1.addEventListener("click", () => {
  p1.style.background = "green";
});
button.addEventListener("click", () => {
  p1.style.background = "white";
});
```

{{ EmbedLiveSample('Modify_an_elements_style') }}

متد {{domxref("window.getComputedStyle", "getComputedStyle()")}} روی شیء `document.defaultView` همهٔ استایل‌هایی را برمی‌گرداند که واقعاً برای یک عنصر محاسبه شده‌اند.

## استفاده از متد setAttribute

توجه داشته باشید که می‌توانید استایل یک عنصر را نیز با گرفتن ارجاعی به آن و سپس استفاده از متد [`setAttribute`](/en-US/docs/Web/API/Element/setAttribute) برای تعیین ویژگی CSS و مقدار آن تغییر دهید.

```js
const el = document.getElementById("some-element");
el.setAttribute("style", "background-color:darkblue;");
```

با این حال، توجه داشته باشید که `setAttribute` همهٔ ویژگی‌های `style` دیگری را که قبلاً در شیء `style` عنصر تعریف شده باشند حذف می‌کند. اگر عنصر `some-element` در بالا یک ویژگی `style` درونخطی مانند `style="font-size: 18px"` داشت، آن مقدار با استفاده از `setAttribute` حذف می‌شود.