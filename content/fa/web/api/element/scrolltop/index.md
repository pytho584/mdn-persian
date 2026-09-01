---
title: "Element: scrollTop property"
slug: Web/API/Element/scrollTop
page-type: web-api-instance-property
browser-compat: api.Element.scrollTop
---

{{APIRef("DOM")}}

ویژگی **`scrollTop`** در رابط {{domxref("Element")}} تعداد پیکسل‌هایی را که محتوای یک عنصر از لبه بالایی آن اسکرول شده است، دریافت یا تنظیم می‌کند. این مقدار در مرورگرهای مدرن با دقت زیرپیکسلی محاسبه می‌شود؛ به این معنی که لزوماً یک عدد صحیح نیست.

## مقدار

یک مقدار ممیز شناور با دقت دوگانه که نشان می‌دهد عنصر در حال حاضر از مبدأ، به‌صورت عمودی چند پیکسل اسکرول شده است. مقدار مثبت به این معنی است که عنصر به سمت پایین اسکرول شده (برای نمایش محتوای بیشتر در پایین). اگر عنصر اصلاً به بالا یا پایین اسکرول نشده باشد، `scrollTop` برابر با `0` است. اگر سند، سند فعال نباشد، مقدار بازگشتی `0` خواهد بود. اگر سند روی دستگاهی با دقت زیرپیکسلی رندر شود، مقدار بازگشتی نیز زیرپیکسلی خواهد بود و ممکن است شامل جزء اعشاری باشد.

ممکن است `scrollTop` منفی باشد اگر عنصر بتواند از بلوک شامل اولیه به سمت بالا اسکرول شود. برای مثال، اگر {{cssxref("flex-direction")}} عنصر برابر با `column-reverse` باشد و محتوا به سمت بالا رشد کند، `scrollTop` وقتی اسکرول‌بار در پایین‌ترین موقعیت خود قرار دارد (در ابتدای محتوای اسکرول‌شده) برابر با `0` است و با اسکرول به سمت انتهای محتوا، به‌طور فزاینده‌ای منفی می‌شود.

سافاری به اسکرول بیش از حد با به‌روزرسانی `scrollTop` فراتر از حداکثر موقعیت اسکرول پاسخ می‌دهد (مگر اینکه افکت پیش‌فرض «جهش» غیرفعال شده باشد، مثلاً با تنظیم {{cssxref("overscroll-behavior")}} روی `none`)؛ در حالی که کروم و فایرفاکس چنین نمی‌کنند. برای مثال، `scrollTop` می‌تواند در سافاری فقط با ادامه اسکرول به بالا وقتی عنصر از قبل در بالای صفحه است، منفی شود.

ویژگی `scrollTop` قابل تنظیم است و باعث می‌شود عنصر به موقعیت عمودی مشخص‌شده اسکرول شود، به همان روشی که از {{domxref("Element.scroll()")}} با `behavior: "auto"` استفاده می‌شود.

## مثال‌ها

### اسکرول یک عنصر

در این مثال، سعی کنید ظرف را با حاشیه خط‌چین اسکرول کنید و ببینید که مقدار `scrollTop` چگونه تغییر می‌کند.

#### HTML

```html
<div id="container">
  <p>
    Far out in the uncharted backwaters of the unfashionable end of the western
    spiral arm of the Galaxy lies a small unregarded yellow sun. Orbiting this
    at a distance of roughly ninety-two million miles is an utterly
    insignificant little blue green planet whose ape-descended life forms are so
    amazingly primitive that they still think digital watches are a pretty neat
    idea.
  </p>
</div>

<div id="output">scrollTop: 0</div>
```

#### CSS

```css
#container {
  overflow: scroll;
  height: 150px;
  width: 150px;
  border: 5px dashed orange;
}

#output {
  padding: 1rem 0;
}
```

#### JavaScript

```js
const container = document.querySelector("#container");
const output = document.querySelector("#output");

container.addEventListener("scroll", (event) => {
  output.textContent = `scrollTop: ${container.scrollTop}`;
});
```

#### نتیجه

{{EmbedLiveSample("Scrolling_an_element", 400, 250)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [تعیین ابعاد عناصر](/en-US/docs/Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements)
- {{domxref("HTMLElement.offsetTop")}}
- {{domxref("Element.clientTop")}}
- {{domxref("Element.scrollHeight")}}
- {{domxref("Element.scrollWidth")}}
- {{domxref("Element.scrollLeft")}}
- {{domxref("Element.getBoundingClientRect()")}}
- {{domxref("Element.scrollTo()")}}