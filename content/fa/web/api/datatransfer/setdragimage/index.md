---
title: "DataTransfer: setDragImage() method"
short-title: setDragImage()
slug: Web/API/DataTransfer/setDragImage
page-type: web-api-instance-method
browser-compat: api.DataTransfer.setDragImage
---

{{APIRef("HTML Drag and Drop API")}}

هنگامی که یک عملیات کشیدن (drag) رخ می‌دهد، یک تصویر نیمه‌شفاف از هدف کشیدن (عنصری که رویداد {{domxref("HTMLElement/dragstart_event", "dragstart")}} روی آن فعال می‌شود) تولید شده و در طول کشیدن، موس را دنبال می‌کند. این تصویر به‌طور خودکار ساخته می‌شود، بنابراین نیازی به ایجاد آن ندارید. با این حال، اگر تصویر سفارشی‌ای مد نظر باشد، می‌توان از متد **`DataTransfer.setDragImage()`** برای تنظیم تصویر سفارشی استفاده کرد. این تصویر معمولاً یک عنصر {{HTMLElement("img")}} خواهد بود، اما می‌تواند یک {{HTMLElement("canvas")}} یا هر عنصر قابل مشاهدهٔ دیگری نیز باشد.

مختصات `x` و `y` متد نحوهٔ نمایش تصویر نسبت به اشاره‌گر موس را مشخص می‌کنند. این مختصات، offset درون تصویر را تعیین می‌کنند که مکان قرارگیری مکان‌نمای موس در آن نقطه باشد. برای مثال، برای نمایش تصویر به‌طوری که اشاره‌گر دقیقاً در مرکز آن قرار گیرد، از مقادیری معادل نصف عرض و نصف ارتفاع تصویر استفاده کنید.

این متد باید درونیابندهٔ رویداد {{domxref("HTMLElement/dragstart_event", "dragstart")}} فراخوانی شود.

## نحو

```js-nolint
setDragImage(imgElement, xOffset, yOffset)
```

### پارامترها

- `imgElement`
  - : یک عنصر {{domxref("Element")}} تصویری که برای تصویر بازخورد کشیدن استفاده می‌شود.

    اگر {{domxref("Element")}} یک عنصر img باشد، بیت‌مپ ذخیره‌گاه دادهٔ کشیدن را به تصویر آن عنصر (در اندازهٔ ذاتی خود) تنظیم می‌کند؛ در غیر این صورت، بیت‌مپ ذخیره‌گاه دادهٔ کشیدن را به تصویری که از عنصر داده شده تولید می‌شود تنظیم می‌کند (مکانیزم دقیق این کار در حال حاضر مشخص نشده است).

    توجه: اگر {{domxref("Element")}} یک {{domxref("HTMLElement")}} موجود باشد، باید در viewport قابل مشاهده باشد تا به‌عنوان تصویر بازخورد کشیدن نمایش داده شود. همچنین می‌توانید یک عنصر DOM جدید که ممکن است خارج از صفحه باشد، به‌طور خاص برای این منظور ایجاد کنید.

- `xOffset`
  - : یک `long` که offset افقی درون تصویر را نشان می‌دهد.
- `yOffset`
  - : یک `long` که offset عمودی درون تصویر را نشان می‌دهد.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

### استفاده از setDragImage()

```html
<div>
  <p id="source" draggable="true">
    این عنصر را انتخاب کنید، آن را به محل رها کردن بکشید و سپس انتخاب را رها کنید
    تا عنصر جابجا شود.
  </p>
</div>
<div id="target">محل رها کردن</div>
```

```css
div {
  margin: 0em;
  padding: 2em;
}
#source {
  color: blue;
  border: 1px solid black;
}
#target {
  border: 1px solid black;
}
```

```js
const source = document.getElementById("source");
const target = document.getElementById("target");

// یک تصویر ایجاد کرده و از آن برای تصویر کشیدن استفاده کنید
// از URL تصویر دلخواه خود استفاده کنید
const img = new Image();
img.src = "/shared-assets/images/examples/favicon32.png";

source.addEventListener("dragstart", (ev) => {
  // قالب و دادهٔ کشیدن را تنظیم کنید. از id هدف رویداد برای داده استفاده کنید
  ev.dataTransfer.setData("text/plain", ev.target.id);
  ev.dataTransfer.setDragImage(img, 10, 10);
});

target.addEventListener("dragover", (ev) => {
  ev.preventDefault();
});

target.addEventListener("drop", (ev) => {
  ev.preventDefault();
  // داده را دریافت کنید، که id هدف رها کردن است
  const data = ev.dataTransfer.getData("text");
  ev.target.appendChild(document.getElementById(data));
});
```

{{EmbedLiveSample("Using setDragImage", "", 300)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [کشیدن و رها کردن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API)
- [عملیات کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations)
- [کار با ذخیره‌گاه دادهٔ کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store)