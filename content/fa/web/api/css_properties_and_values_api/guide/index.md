---
title: "Using the CSS properties and values API"
slug: Web/API/CSS_Properties_and_Values_API/guide
page-type: guide
browser-compat: api.CSS.registerProperty_static
---

{{DefaultAPISidebar("CSS Properties and Values API")}}

**CSS Properties and Values API** — بخشی از مجموعه‌APIهای [CSS Houdini](/en-US/docs/Web/API/Houdini_APIs) — امکان ثبت [خصوصیات سفارشی CSS](/en-US/docs/Web/CSS/Reference/Properties/--*) را فراهم می‌کند، که بررسی نوع خصوصیت، مقادیر پیش‌فرض، و خصوصیاتی که مقدار خود را به ارث می‌برند یا نمی‌برند، امکان‌پذیر می‌سازد.

## ثبت یک خصوصیت سفارشی

ثبت یک خصوصیت سفارشی به شما امکان می‌دهد به مرورگر بگویید که خصوصیت سفارشی چگونه باید رفتار کند: چه نوع‌هایی مجاز هستند، آیا خصوصیت سفارشی مقدار خود را به ارث می‌برد، و مقدار پیش‌فرض خصوصیت سفارشی چیست. دو روش برای ثبت یک خصوصیت وجود دارد: در [جاوااسکریپت](/en-US/docs/Web/JavaScript) یا در [CSS](/en-US/docs/Web/CSS).

### CSS.registerProperty

کد زیر یک [خصوصیت سفارشی](/en-US/docs/Web/CSS/Reference/Properties/--*) به نام `--my-prop` را با استفاده از {{domxref('CSS/registerProperty_static', 'CSS.registerProperty')}} ثبت می‌کند. `--my-prop` از نحو رنگ CSS استفاده می‌کند، مقدار پیش‌فرض آن `#c0ffee` خواهد بود، و مقدار خود را به ارث نمی‌برد:

```js
window.CSS.registerProperty({
  name: "--my-prop",
  syntax: "<color>",
  inherits: false,
  initialValue: "#c0ffee",
});
```

### @property

همین ثبت می‌تواند در CSS نیز انجام شود. کد زیر یک [خصوصیت سفارشی](/en-US/docs/Web/CSS/Reference/Properties/--*) به نام `--my-prop` را با استفاده از [قاعده at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) {{cssxref('@property')}} ثبت می‌کند. `--my-prop` از نحو رنگ CSS استفاده می‌کند، مقدار پیش‌فرض آن `#c0ffee` خواهد بود، و مقدار خود را به ارث نمی‌برد:

```css
@property --my-prop {
  syntax: "<color>";
  inherits: false;
  initial-value: #c0ffee;
}
```

## استفاده از خصوصیات سفارشی ثبت‌شده

یکی از مزایای ثبت یک خصوصیت این است که مرورگر اکنون می‌داند چگونه خصوصیت سفارشی شما را در مواردی مانند transitions مدیریت کند! وقتی یک خصوصیت ثبت نشده باشد، مرورگر نمی‌داند چگونه با آن رفتار کند، بنابراین فرض می‌کند هر مقداری قابل استفاده است و بنابراین نمی‌تواند آن را انیمیت کند. اما وقتی یک خصوصیت دارای نحو ثبت‌شده است، مرورگر می‌تواند بر اساس آن نحو بهینه‌سازی کند، از جمله توانایی انیمیت آن!

در این مثال، خصوصیت سفارشی `--registered` با استفاده از نحو `<color>` ثبت شده است و سپس در یک گرادیان خطی استفاده شده است. آن خصوصیت در هنگام hover یا focus به یک رنگ دیگر transition می‌کند. توجه کنید که transition با خصوصیت ثبت‌شده کار می‌کند اما با خصوصیت ثبت‌نشده کار نمی‌کند!

### HTML

```html
<button class="registered">پس‌زمینه ثبت‌شده</button>
<button class="unregistered">پس‌زمینه ثبت‌نشده</button>
```

### CSS

```css
.registered {
  --registered: #c0ffee;
  background-image: linear-gradient(to right, white, var(--registered));
  transition: --registered 1s ease-in-out;
}

.registered:hover,
.registered:focus {
  --registered: #b4d455;
}

.unregistered {
  --unregistered: #c0ffee;
  background-image: linear-gradient(to right, white, var(--unregistered));
  transition: --unregistered 1s ease-in-out;
}

.unregistered:hover,
.unregistered:focus {
  --unregistered: #b4d455;
}

button {
  height: 40vh;
  display: block;
  width: 100%;
  font-size: 3vw;
}
```

### JavaScript

```js
window.CSS.registerProperty({
  name: "--registered",
  syntax: "<color>",
  inherits: false,
  initialValue: "red",
});
```

### نتیجه

{{EmbedLiveSample("Using_registered_custom_properties", 320, 320)}}

اگرچه از نظر عملیاتی دقیق نیست، یک راه خوب برای فکر کردن به تفاوت بین خصوصیت ثبت‌نشده در مثال بالا و خصوصیت ثبت‌شده، تفاوت بین یک {{cssxref('custom-ident')}} و یک عدد هنگام تلاش برای انیمیت {{cssxref('height')}} است. شما نمی‌توانید از `auto` به یک عدد transition یا انیمیت کنید زیرا مرورگر مقدار `auto` را تا زمانی که محاسبه نشود نمی‌داند. با یک خصوصیت ثبت‌نشده، مرورگر نیز نمی‌داند مقدار _ممکن است_ چه باشد تا زمانی که محاسبه شود، و به همین دلیل نمی‌تواند یک transition از یک مقدار به مقدار دیگر تنظیم کند. اما وقتی ثبت شده باشد، شما به مرورگر گفته‌اید که چه نوع مقداری را انتظار داشته باشد، و چون این را می‌داند، می‌تواند transitions را به درستی تنظیم کند.

## نکات مهم

دو نکته مهم در هنگام ثبت یک خصوصیت وجود دارد. اول اینکه، وقتی یک خصوصیت ثبت شد، راهی برای به‌روزرسانی آن وجود ندارد، و تلاش برای ثبت مجدد آن با [جاوااسکریپت](/en-US/docs/Web/JavaScript) یک خطا ایجاد می‌کند که نشان می‌دهد قبلاً تعریف شده است.

دوم اینکه، برخلاف خصوصیات استاندارد، خصوصیات ثبت‌شده هنگام تجزیه (parsing) اعتبارسنجی نمی‌شوند. بلکه هنگام محاسبه (computed) اعتبارسنجی می‌شوند. این بدان معناست که هم مقادیر نامعتبر هنگام بررسی خصوصیات عنصر به عنوان نامعتبر ظاهر نخواهند شد، و هم اینکه شامل یک خصوصیت نامعتبر بعد از یک خصوصیت معتبر باعث بازگشت به خصوصیت معتبر نمی‌شود. با این حال، یک خصوصیت نامعتبر به مقدار پیش‌فرض ثبت‌شده خود بازمی‌گردد.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ثبت خصوصیات سفارشی با CSS](/en-US/docs/Web/CSS/Guides/Properties_and_values_API/Registering_properties)