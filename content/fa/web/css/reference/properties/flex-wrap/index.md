---
title: "flex-wrap CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/flex-wrap"
translated_by: "n8n + AI"
---

ویژگی **`flex-wrap`** در CSS مشخص می‌کند که آیتم‌های یک flex container تنها در یک خط باقی بمانند یا اجازهٔ شکستن به چند خط را داشته باشند. اگر شکستن خط مجاز باشد، جهت چیدمان خطوط نیز تعیین می‌شود.

می‌توان با shorthand ویژگی {{cssxref("flex-flow")}}، هر دو ویژگی `flex-wrap` و {{CSSXRef("flex-direction")}} را به‌طور هم‌زمان تنظیم کرد. این دو ویژگی به ترتیب محور اصلی و محور متقاطع flex container را تعریف می‌کنند.

## نحوهٔ نوشتن

```css
flex-wrap: nowrap; /* مقدار پیش‌فرض */
flex-wrap: wrap;
flex-wrap: wrap-reverse;

/* مقادیر سراسری */
flex-wrap: inherit;
flex-wrap: initial;
flex-wrap: revert;
flex-wrap: revert-layer;
flex-wrap: unset;
```

### مقادیر

ویژگی `flex-wrap` یکی از کلمات کلیدی زیر را می‌پذیرد:

- `nowrap`
  - : آیتم‌های flex در یک خط چیده می‌شوند. این وضعیت ممکن است باعث سرریز شدن flex container شود. نقطهٔ شروع محور متقاطع (cross-start) معادل `inline-start` یا `block-start` است (بسته به مقدار {{cssxref("flex-direction")}}). این مقدار پیش‌فرض است.
- `wrap`
  - : آیتم‌ها به چند خط می‌شکنند. نقطهٔ شروع محور متقاطع معادل `inline-start` یا `block-start` است که با توجه به [حالت نوشتار](/en-US/docs/Web/CSS/Guides/Writing_modes) جاری و مقدار `flex-direction` تعیین می‌شود.
- `wrap-reverse`
  - : رفتاری مشابه `wrap` دارد، اما جهت شروع و پایان محور متقاطع معکوس می‌شود.

## مثال‌ها

### تنظیم مقادیر مختلف flex-wrap برای یک flex container

#### HTML

```html
<h4>نمونه‌ای برای flex-wrap:wrap</h4>
<div class="content">
  <div class="red">1</div>
  <div class="green">2</div>
  <div class="blue">3</div>
</div>
<h4>نمونه‌ای برای flex-wrap:nowrap</h4>
<div class="content1">
  <div class="red">1</div>
  <div class="green">2</div>
  <div class="blue">3</div>
</div>
<h4>نمونه‌ای برای flex-wrap:wrap-reverse</h4>
<div class="content2">
  <div class="red">1</div>
  <div class="green">2</div>
  <div class="blue">3</div>
</div>
```

#### CSS

```css
/* استایل‌های مشترک */
.content,
.content1,
.content2 {
  color: white;
  font: 100 24px/100px sans-serif;
  height: 150px;
  width: 897px;
  text-align: center;
}

.content div,
.content1 div,
.content2 div {
  height: 50%;
  width: 300px;
}
.red {
  background: orangered;
}
.green {
  background: yellowgreen;
}
.blue {
  background: steelblue;
}

/* استایل‌های flexbox */
.content {
  display: flex;
  flex-wrap: wrap;
}
.content1 {
  display: flex;
  flex-wrap: nowrap;
}
.content2 {
  display: flex;
  flex-wrap: wrap-reverse;
}
```

#### نتیجه

در اولین container با `flex-wrap: wrap`، آیتم‌ها در صورت نبود فضای کافی به خط بعد منتقل می‌شوند. در دومین container با `nowrap` همهٔ آیتم‌ها در یک خط فشرده می‌مانند و ممکن است موجب سرریز شوند. در سومین container با `wrap-reverse` خطوط از پایین به بالا چیده می‌شوند.

## همچنین ببینید

- [مفاهیم پایه‌ای flexbox](/en-US/docs/Web/CSS/Guides/Basic_concepts_of_flexbox)
- [تسلط بر wrapping آیتم‌های flex](/en-US/docs/Web/CSS/Guides/Mastering_wrapping_of_flex_items)

- [مفاهیم پایه‌ای flexbox](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Basic_concepts)
- [تسلط بر wrapping آیتم‌های flex](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Wrapping_items)
- ماژول [چیدمان جعبه‌ای انعطاف‌پذیر CSS](/en-US/docs/Web/CSS/Guides/Flexible_box_layout)