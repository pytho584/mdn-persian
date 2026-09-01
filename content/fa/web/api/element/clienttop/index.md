---
title: "Element: clientTop property"
short-title: clientTop
slug: Web/API/Element/clientTop
page-type: web-api-instance-property
browser-compat: api.Element.clientTop
---

{{ APIRef("DOM") }}

ویژگی فقط‌خواندنی **`clientTop`** از رابط {{domxref("Element")}}، عرض حاشیهٔ بالایی یک عنصر را بر حسب پیکسل برمی‌گرداند.

هر آنچه بین `offsetTop` و `clientTop` قرار دارد، فقط border عنصر است. دلیلش این است که `offsetTop` محل شروع بالای border (نه margin) را نشان می‌دهد، در حالی که ناحیهٔ کلاینت بلافاصله بعد از border شروع می‌شود و شامل padding نیز هست. بنابراین مقدار `clientTop` همیشه با `border-top-width` گردشده به عدد صحیح برابر است. به‌عنوان مثال، اگر `border-top-width` محاسبه‌شده صفر باشد، `clientTop` نیز صفر است.

## مقدار

یک عدد صحیح.

## مثال‌ها

در مثال زیر، ناحیهٔ کلاینت پس‌زمینهٔ سفید و یک `border-top` سیاه به ضخامت ۲۴px دارد. مقدار `clientTop` فاصله‌ای است از جایی که ناحیهٔ margin (زرد) تمام می‌شود تا جایی که نواحی padding و content (سفید) شروع می‌شوند؛ یعنی ۲۴px.

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
  border-top: 24px black solid;
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
- {{domxref("HTMLElement.offsetTop")}}
- {{domxref("Element.scrollTop")}}
- {{domxref("Element.clientHeight")}}
- {{domxref("Element.clientWidth")}}
- {{domxref("Element.clientLeft")}}
- {{domxref("Element.getBoundingClientRect()")}}