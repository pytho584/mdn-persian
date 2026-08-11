---
title: "CSS custom properties for cascading variables"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Cascading_variables"
translated_by: "n8n + AI"
---

```markdown
ماژول **CSS custom properties for cascading variables** پشتیبانی از متغیرهای آبشاری (cascading variables) را در ویژگی‌های CSS اضافه می‌کند. این ماژول به شما امکان می‌دهد خاصیت‌های سفارشی (custom properties) برای تعریف این متغیرها ایجاد کنید، همراه با سازوکارهایی برای استفاده از خاصیت‌های سفارشی به عنوان مقدار ویژگی‌های دیگر CSS.

وقتی با CSS کار می‌کنید، اغلب مجبورید مقادیر تکراری مخصوص پروژه را دوباره استفاده کنید؛ مثلاً عرض‌های مناسب برای layout یا مجموعه‌ای از رنگ‌ها برای طرح رنگ. یکی از روش‌های مدیریت تکرار در stylesheetها این است که یک مقدار را یکبار تعریف کرده و در جاهای دیگر چندین بار استفاده کنید. Custom properties به شما امکان می‌دهند متغیرهای سفارشی ایجاد و تعریف کنید که قابل استفاده مجدد باشند، قوانین پیچیده یا تکراری را ساده کرده و خوانایی و نگهداری را آسان‌تر می‌کنند. برای مثال، `--dark-grey-text` و `--dark-background` از رنگ‌های هگزادسیمال مانند `#323831` قابل‌فهم‌تر هستند، و زمینه استفاده از آن‌ها نیز واضح‌تر است.

## Custom properties در عمل

برای دیدن نحوه استفاده از custom properties، اسلایدر ورودی را به چپ و راست حرکت دهید.

```html hidden
<div class="container">
  <div id="color-1">--hue</div>
  <div id="color-2">--hue + 10</div>
  <div id="color-3">--hue + 20</div>
  <div id="color-4">--hue + 30</div>
  <div id="color-5">--hue + 40</div>
  <div id="color-6">--hue + 50</div>
  <div id="color-7">--hue + 60</div>
  <div id="color-8">--hue + 70</div>
</div>
<input type="range" min="0" max="360" value="0" step="0.1" id="hue" />
```

```js hidden
const hue = document.querySelector("#hue");

const updateHue = () => {
  document.documentElement.style.setProperty("--hue", hue.value);
};

hue.addEventListener("input", updateHue);
```

```css hidden
.container {
  display: grid;
  font-family: sans-serif;
  color: white;
  gap: 0.5rem;
  grid-template-columns: repeat(4, 1fr);
  margin-bottom: 1rem;
}
.container div {
  border-radius: 0.5rem;
  padding: 1rem;
}

input {
  width: 100%;
  margin: 0;
}

:root {
  --hue: 0;
}

#color-1 {
  background-color: hsl(var(--hue) 50% 50%);
}
#color-2 {
  background-color: hsl(calc(var(--hue) + 10) 50% 50%);
}
#color-3 {
  background-color: hsl(calc(var(--hue) + 20) 50% 50%);
}
#color-4 {
  background-color: hsl(calc(var(--hue) + 30) 50% 50%);
}
#color-5 {
  background-color: hsl(calc(var(--hue) + 40) 50% 50%);
}
#color-6 {
  background-color: hsl(calc(var(--hue) + 50) 50% 50%);
}
#color-7 {
  background-color: hsl(calc(var(--hue) + 60) 50% 50%);
}
#color-8 {
  background-color: hsl(calc(var(--hue) + 70) 50% 50%);
}
```

در این نمونه‌های رنگی، `background-color` با استفاده از تابع `hsl()` به صورت `hsl(var(--hue) 50% 50%)` تنظیم شده است. هر نمونه رنگی مقدار hue را ۱۰ درجه افزایش می‌دهد مانند `calc(var(--hue) + 10)`، `calc(var(--hue) + 20)` و غیره. با تغییر مقدار اسلایدر از ۰ تا ۳۶۰، مقدار خاصیت سفارشی `--hue` (custom property) با استفاده از `calc` به‌روز می‌شود و رنگ پس‌زمینه هر جعبه در grid نیز تغییر می‌کند.

## مرجع

### Properties

- [`--*`](/en-US/docs/Web/CSS/Reference/Properties/--*)

### Functions

- [`var()`](/en-US/docs/Web/CSS/var)

## راهنماها

- [استفاده از خاصیت‌های سفارشی CSS (متغیرها)](/en-US/docs/Web/CSS/Guides/Cascading_variables/Using_custom_properties)
  - : نحوه استفاده از custom properties در CSS و JavaScript را با نکاتی درباره مدیریت مقادیر تعریف‌نشده و نامعتبر، fallbackها و وراثت توضیح می‌دهد.

- [خاصیت‌های سفارشی نامعتبر](/en-US/docs/Web/CSS/Guides/Syntax/Error_handling#invalid_custom_properties)
  - : توضیح می‌دهد که مرورگرها چگونه مقادیر خاصیت را زمانی که مقدار یک custom property از نوع داده نامعتبر برای آن خاصیت است، مدیریت می‌کنند.

## مفاهیم مرتبط
```

## ماژول CSS Properties and Values API

- at-rule @property
- متد `CSS.registerProperty()`

## همچنین ببینید

- [CSS cascading and inheritance](/en-US/docs/Web/CSS/Guides/Cascade) module
- [CSS `env()`](/en-US/docs/Web/CSS/Reference/Values/env) function
- [CSS `calc()`](/en-US/docs/Web/CSS/Reference/Values/calc) function
- [`getPropertyValue()`](/en-US/docs/Web/API/CSSStyleDeclaration/getPropertyValue) method