---
title: "Element: scrollLeft property"
---

---
title: "Element: scrollLeft property"
short-title: scrollLeft
slug: Web/API/Element/scrollLeft
page-type: web-api-instance-property
browser-compat: api.Element.scrollLeft
---

{{APIRef("DOM")}}

خاصیت **`scrollLeft`** از رابط {{domxref("Element")}} تعداد پیکسل‌هایی را که محتوای یک عنصر از لبه چپ خود اسکرول شده است، دریافت یا تنظیم می‌کند. این مقدار در مرورگرهای مدرن با دقت زیرپیکسلی است، یعنی لزوماً یک عدد صحیح نیست.

## مقدار

یک مقدار ممیز شناور با دقت دوگانه که نشان می‌دهد عنصر در حال حاضر چند پیکسل از مبدأ به صورت افقی اسکرول شده است. مقدار مثبت به این معنی است که عنصر به سمت راست اسکرول شده است (تا محتوای بیشتری در سمت راست نمایش داده شود). اگر عنصر اصلاً به چپ یا راست اسکرول نشده باشد، `scrollLeft` برابر ۰ است. اگر سند، سند فعال نباشد، مقدار بازگشتی ۰ خواهد بود. اگر سند روی دستگاهی با دقت زیرپیکسلی رندر شده باشد، مقدار بازگشتی نیز دارای دقت زیرپیکسلی بوده و ممکن است شامل یک جزء اعشاری باشد.

امکان منفی شدن `scrollLeft` وجود دارد اگر عنصر بتواند از بلوک محتوی اولیه به سمت چپ اسکرول شود. به عنوان مثال، اگر {{cssxref("direction")}} عنصر `rtl` (راست‌به‌چپ) باشد و محتوا به سمت چپ رشد کند، `scrollLeft` وقتی نوار اسکرول در سمت‌راست‌ترین موقعیت خود (در ابتدای محتوای اسکرول‌شده) قرار دارد، برابر `0` خواهد بود و با اسکرول به سمت انتهای محتوا، به طور فزاینده‌ای منفی می‌شود.

Safari به اسکرول بیش از حد با به‌روزرسانی `scrollLeft` فراتر از حداکثر موقعیت اسکرول پاسخ می‌دهد (مگر اینکه اثر پیش‌فرض «جهش» غیرفعال شده باشد، مثلاً با تنظیم {{cssxref("overscroll-behavior")}} روی `none`)، در حالی که Chrome و Firefox این کار را نمی‌کنند.

خاصیت `scrollLeft` قابل تنظیم است، که باعث می‌شود عنصر به موقعیت افقی مشخص‌شده اسکرول شود، به همان روشی که با استفاده از {{domxref("Element.scroll()")}} با `behavior: "auto"` انجام می‌شود.

## مثال‌ها

### HTML

```html
<div id="container">
  <div id="content">Click the button to slide right!</div>
</div>

<button id="slide" type="button">Slide right</button>
```

### CSS

```css
#container {
  width: 100px;
  height: 100px;
  border: 1px solid #cccccc;
  overflow-x: scroll;
}

#content {
  width: 250px;
  background-color: #cccccc;
}
```

### JavaScript

```js
const button = document.getElementById("slide");

button.onclick = () => {
  document.getElementById("container").scrollLeft += 20;
};
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [تعیین ابعاد عناصر](/en-US/docs/Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements)
- {{domxref("HTMLElement.offsetLeft")}}
- {{domxref("Element.clientLeft")}}
- {{domxref("Element.scrollHeight")}}
- {{domxref("Element.scrollWidth")}}
- {{domxref("Element.scrollTop")}}
- {{domxref("Element.getBoundingClientRect()")}}
- {{domxref("Element.scrollTo()")}}