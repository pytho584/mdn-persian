---
title: "Element: clientLeft property"
---

---
title: "Element: clientLeft property"
short-title: clientLeft
slug: Web/API/Element/clientLeft
page-type: web-api-instance-property
browser-compat: api.Element.clientLeft
---

{{ APIRef("DOM") }}

ویژگی فقط‌خواندنی **`clientLeft`** در رابط {{domxref("Element")}} عرض حاشیه چپ یک عنصر را بر حسب پیکسل برمی‌گرداند. اگر جهت متن عنصر راست‌به‌چپ باشد و سرریزی (overflow) وجود داشته باشد که باعث رندر شدن اسکرول‌بار عمودی در سمت چپ شود، این مقدار شامل عرض آن اسکرول‌بار عمودی نیز می‌شود. `clientLeft` شامل حاشیه بیرونی چپ (margin) یا فاصله داخلی چپ (padding) نمی‌شود.

> [!NOTE]
> وقتی عنصری دارای `display: inline` باشد، `clientLeft` بدون توجه به حاشیه عنصر مقدار `0` برمی‌گرداند.

## مقدار

یک عدد صحیح.

## مثال‌ها

در مثال زیر، ناحیه کلاینت دارای پس‌زمینه سفید و یک `border-left` به رنگ مشکی با ضخامت ۲۴ پیکسل است. مقدار `clientLeft` فاصله‌ای است که از انتهای ناحیه حاشیه بیرونی (زرد) شروع شده و به ابتدای ناحیه padding و محتوا (سفید) ختم می‌شود؛ یعنی ۲۴ پیکسل.

### HTML

```html
<div id="container">
  <div id="contained">
    <p>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
      tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
      veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
      commodo consequat.
    </p>
  </div>
</div>
```

### CSS

```css
#container {
  margin: 3rem;
  background-color: rgb(255 255 204);
  border: 4px dashed black;
}

#contained {
  margin: 1rem;
  border-left: 24px black solid;
  padding: 0px 28px;
  overflow: auto;
  background-color: white;
}
```

### نتیجه

{{EmbedLiveSample("Examples", 400, 350)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [تعیین ابعاد عناصر](/en-US/docs/Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements)
- {{domxref("HTMLElement.offsetLeft")}}
- {{domxref("Element.scrollLeft")}}
- {{domxref("Element.clientHeight")}}
- {{domxref("Element.clientWidth")}}
- {{domxref("Element.clientTop")}}
- {{domxref("Element.getBoundingClientRect()")}}