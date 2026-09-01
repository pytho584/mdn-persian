---
title: "Highlight: priority property"
short-title: priority
slug: Web/API/Highlight/priority
page-type: web-api-instance-property
browser-compat: api.Highlight.priority
---

{{APIRef("CSS Custom Highlight API")}}

ویژگی `priority` از رابط {{domxref("Highlight")}} عددی است که برای تعیین اینکه در بخش‌های همپوشان، سبک‌های کدام هایلایت باید برای حل تعارض‌های سبک استفاده شوند، به کار می‌رود. هایلایت‌هایی که عدد `priority` بالاتری دارند، نسبت به هایلایت‌هایی با `priority` کمتر اولویت دارند.

می‌توان اشیاء {{domxref("AbstractRange")}} را ایجاد کرد که در یک سند با یکدیگر همپوشانی دارند.

هنگامی که محدوده‌های همپوشان متعلق به چندین شیء متفاوت {{domxref("Highlight")}} باشند و آن هایلایت‌ها با شبه‌عنصرهای {{cssxref("::highlight")}} استایل‌بندی شده باشند، ممکن است سبک‌هایی متعارض به وجود آید.

اگر دو محدوده متنی همپوشانی داشته باشند و هر دو با استفاده از {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}} هایلایت شده باشند و هر دو با ویژگی `color` در CSS استایل‌بندی شده باشند، مرورگر باید تصمیم بگیرد که در بخش همپوشان از کدام رنگ برای استایل‌بندی متن استفاده کند.

اگر `priority` تنظیم نشده باشد، همه هایلایت‌ها اولویت یکسانی دارند و مرورگر جدیدترین هایلایت ثبت‌شده را برای استایل‌بندی بخش‌های همپوشان انتخاب می‌کند.

توجه داشته باشید که تمام سبک‌های یک هایلایت اعمال می‌شوند و مرورگر فقط زمانی نیاز به حل تعارض دارد که ویژگی‌های یکسانی از CSS توسط چند هایلایت همپوشان استفاده شده باشند. همچنین، حل تعارض سبک هایلایت‌ها به ترتیب ظاهر شدن قواعد شبه‌عنصرهای {{cssxref("::highlight")}} در سورس بستگی ندارد و نیز به این بستگی ندارد که ویژگی‌های CSS با `!important` علامت‌گذاری شده باشند یا خیر.

## مقدار

یک عدد صحیح.

## مثال‌ها

### Default priority

#### HTML

```html
<p>Time is an illusion. Lunchtime doubly so.</p>
```

#### CSS

```css
::highlight(highlight-2) {
  color: blue;
}

::highlight(highlight-1) {
  color: white;
  background: orange;
}
```

#### JavaScript

```js
const text = document.querySelector("p").firstChild;

// Create two overlapping highlights
const range1 = new Range();
range1.setStart(text, 5);
range1.setEnd(text, 25);

const range2 = new Range();
range2.setStart(text, 15);
range2.setEnd(text, 35);

const highlight1 = new Highlight(range1);
const highlight2 = new Highlight(range2);

CSS.highlights.set("highlight-1", highlight1);
CSS.highlights.set("highlight-2", highlight2);
```

#### نتیجه

همان‌طور که در زیر می‌بینید، به‌طور پیش‌فرض، بخشی از گره متنی که دو هایلایت ثبت‌شده در آن همپوشانی دارند، به رنگ آبی نمایش داده می‌شود، زیرا `highlight-2` پس از `highlight-1` ثبت شده است. رنگ پس‌زمینه تعریف‌شده توسط `highlight-1` کل محدوده `range1` را در بر می‌گیرد، زیرا با رنگ پس‌زمینه دیگری تعارضی ندارد.

{{EmbedLiveSample("Default priority")}}

### Setting priority

#### HTML

```html
<button id="prioritize-1" type="button">Prioritize 1</button>
<button id="prioritize-2" type="button">Prioritize 2</button>
<button id="reset" type="button">Reset</button>
<p>Time is an illusion. Lunchtime doubly so.</p>
```

#### CSS

```css
::highlight(highlight-1) {
  background-color: blue;
  color: white;
}

::highlight(highlight-2) {
  background-color: orange;
}
```

#### JavaScript

```js
const text = document.querySelector("p").firstChild;

// Create two overlapping highlights
const range1 = new Range();
range1.setStart(text, 5);
range1.setEnd(text, 25);

const range2 = new Range();
range2.setStart(text, 15);
range2.setEnd(text, 35);

const highlight1 = new Highlight(range1);
const highlight2 = new Highlight(range2);

CSS.highlights.set("highlight-1", highlight1);
CSS.highlights.set("highlight-2", highlight2);

// Add buttons to change the highlight priority.
const prioritize1 = document.querySelector("#prioritize-1");
const prioritize2 = document.querySelector("#prioritize-2");
const reset = document.querySelector("#reset");

prioritize1.addEventListener("click", () => {
  highlight1.priority = 1;
  highlight2.priority = 0;
});

prioritize2.addEventListener("click", () => {
  highlight1.priority = 0;
  highlight2.priority = 1;
});

reset.addEventListener("click", () => {
  highlight1.priority = 0;
  highlight2.priority = 0;
});
```

#### نتیجه

همان‌طور که در زیر می‌بینید، به‌طور پیش‌فرض، بخشی از گره متنی که دو هایلایت ثبت‌شده در آن همپوشانی دارند، به رنگ آبی نمایش داده می‌شود، زیرا `highlight-2` پس از `highlight-1` ثبت شده است.

{{EmbedLiveSample("Setting priority")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: آینده برجسته‌سازی محدوده‌های متنی در وب](https://css-tricks.com/css-custom-highlight-api-early-look/)