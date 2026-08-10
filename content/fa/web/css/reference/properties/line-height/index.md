---
title: "line-height CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/line-height"
translated_by: "n8n + AI"
---

# `line-height`

خصوصیت **`line-height`** در [CSS](/en-US/docs/Web/CSS) ارتفاع یک line box را در [حالت نوشتار افقی](/en-US/docs/Web/CSS/Reference/Properties/writing-mode#vertical-rl) تعیین می‌کند. در حالت نوشتار عمودی، عرض line box را مشخص می‌کند. این خصوصیت معمولاً برای تنظیم فاصلهٔ بین خطوط متن استفاده می‌شود. برای عناصر block-level در حالت افقی، ارتفاع ترجیحی line boxهای درون عنصر را مشخص می‌کند و برای عناصر inline [غیرجایگزین](/en-US/docs/Glossary/Replaced_elements)، ارتفاعی را تعیین می‌کند که برای محاسبهٔ ارتفاع line box به کار می‌رود.

## نحو

```css
/* مقدار کلیدی */
line-height: normal;

/* مقادیر بدون واحد: از ضرب این عدد
در اندازهٔ فونت عنصر استفاده می‌شود */
line-height: 3.5;

/* مقادیر <length> */
line-height: 3em;

/* مقادیر <percentage> */
line-height: 34%;

/* مقادیر سراسری */
line-height: inherit;
line-height: initial;
line-height: revert;
line-height: revert-layer;
line-height: unset;
```

خصوصیت `line-height` به یکی از شکل‌های زیر تعیین می‌شود:

- یک `<number>`
- یک `<length>`
- یک `<percentage>`
- کلیدواژهٔ `normal`.

### مقادیر

- `normal`
  - : بسته به عامل کاربر (user agent) متفاوت است. مرورگرهای دسکتاپ (از جمله فایرفاکس) مقداری پیش‌فرض در حدود **`1.2`** استفاده می‌کنند که به `font-family` عنصر بستگی دارد.
- `<number>` (بدون واحد)
  - : مقدار استفاده‌شده حاصل ضرب این {{cssxref("&lt;number&gt;")}} بدون واحد در اندازهٔ فونت خود عنصر است. مقدار محاسبه‌شده همان `<number>` تعیین‌شده خواهد بود. در بیشتر موارد، **این روش پیشنهادی** برای تنظیم `line-height` است و از نتایج غیرمنتظرهٔ ناشی از وراثت جلوگیری می‌کند.
- `<length>`
  - : مقدار {{cssxref("&lt;length&gt;")}} مشخص‌شده در محاسبهٔ ارتفاع line box به کار می‌رود. مقادیری که با واحد **em** داده شوند ممکن است نتایج غیرمنتظره‌ای ایجاد کنند (مثال زیر را ببینید).
- `<percentage>`
  - : نسبت به اندازهٔ فونت خود عنصر. مقدار محاسبه‌شده حاصل ضرب این {{cssxref("&lt;percentage&gt;")}} در اندازهٔ فونت محاسبه‌شدهٔ عنصر است. مقادیر **درصدی** ممکن است نتایج غیرمنتظره‌ای ایجاد کنند (مثال دوم را در ادامه ببینید).

## دسترس‌پذیری

برای محتوای پاراگراف اصلی، حداقل مقدار `1.5` را برای `line-height` در نظر بگیرید. این کار به افرادی که دچار کم‌بینایی هستند یا مشکلات شناختی مانند دیسلکسی دارند کمک می‌کند. اگر صفحه برای بزرگ‌نمایی متن زوم شود، استفاده از مقدار بدون واحد تضمین می‌کند که ارتفاع خط به‌طور متناسب مقیاس‌بندی شود.

[W3C Understanding WCAG 2.2](https://w3c.github.io/wcag/guidelines/22/#visual-presentation)

## مثال‌ها

### مثال پایه

```css
/* همهٔ دستورات زیر ارتفاع خط نهایی یکسانی دارند */

/* عدد/بدون واحد */
div {
  line-height: 1.2;
  font-size: 10pt;
}

/* طول */
div {
  line-height: 1.2em;
  font-size: 10pt;
}

/* درصد */
div {
  line-height: 120%;
  font-size: 10pt;
}

/* خلاصهٔ font */
div {
  font:
    10pt/1.2 "Bitstream Charter",
    "Georgia",
    serif;
}
```

اغلب، تنظیم `line-height` با استفاده از shorthand `font` (همانطور که در بالا نشان داده شد) راحت‌تر است، اما این کار مستلزم آن است که خصوصیت `font-family` نیز تعیین شده باشد.

### ترجیح استفاده از اعداد بدون واحد برای مقادیر line-height

این مثال نشان می‌دهد که چرا استفاده از مقادیر `<number>` به جای مقادیر `<length>` بهتر است. ما از دو عنصر `<div>` استفاده می‌کنیم. div اول، با حاشیه سبز، از یک مقدار بدون واحد `line-height` استفاده می‌کند. div دوم، با حاشیه قرمز، از مقدار `line-height` تعریف‌شده با واحد `em` استفاده می‌کند.

#### HTML

```html
<div class="box green">
  <h1>با استفاده از line-height بدون واحد از نتایج غیرمنتظره جلوگیری کنید.</h1>
  line-heightهای مبتنی بر طول و درصد، رفتار وراثت ضعیفی دارند.
</div>

<div class="box red">
  <h1>با استفاده از line-height بدون واحد از نتایج غیرمنتظره جلوگیری کنید.</h1>
  line-heightهای مبتنی بر طول و درصد، رفتار وراثت ضعیفی دارند
</div>

<!-- line-height اولین <h1> بر اساس font-size خودش محاسبه می‌شود (30px × 1.1) = 33px -->
<!-- line-height دومین <h1> از font-size div قرمز به دست می‌آید (15px × 1.1) = 16.5px، که احتمالاً چیزی نیست که انتظار دارید -->
```

#### CSS

```css
.green {
  line-height: 1.1;
  border: solid limegreen;
}

.red {
  line-height: 1.1em;
  border: solid red;
}

h1 {
  font-size: 30px;
}

.box {
  width: 18em;
  display: inline-block;
  vertical-align: top;
  font-size: 15px;
}
```

#### نتیجه

### فاصله بین خطوط در حالت‌های نوشتار عمودی

خصوصیت `line-height` می‌تواند برای تنظیم فاصله بین خطوط عمودی در حالت‌های نوشتار عمودی استفاده شود.

```html hidden
<div class="haiku">
  古池や蛙飛び込む水の音<br />
  ふるいけやかわずとびこむみずのおと<br />
  富士の風や扇にのせて江戸土産<br />
  ふじのかぜやおうぎにのせてえどみやげ<br />
</div>

<div class="haiku wide">
  古池や蛙飛び込む水の音<br />
  ふるいけやかわずとびこむみずのおと<br />
  富士の風や扇にのせて江戸土産<br />
  ふじのかぜやおうぎにのせてえどみやげ<br />
</div>
```

```css
.haiku {
  border: 1px solid;
  margin-bottom: 1rem;
  padding: 0.5rem;
  background-color: wheat;

  writing-mode: vertical-rl;
}

.wide {
  line-height: 2;
}
```

#### نتیجه

## همچنین ببینید

- `font`، `font-size`
- `Leading`