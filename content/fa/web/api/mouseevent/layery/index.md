---
title: "MouseEvent: layerY property"
short-title: layerY
slug: Web/API/MouseEvent/layerY
page-type: web-api-instance-property
status:
  - non-standard
browser-compat: api.MouseEvent.layerY
---

{{APIRef("Pointer Events")}}{{Non-standard_Header}}

خاصیت فقط-خواندنی **`MouseEvent.layerY`** مختصات عمودی رویداد را نسبت به لایه‌ی فعلی برمی‌گرداند.

این خاصیت اسکرول صفحه را در نظر می‌گیرد و مقداری را برمی‌گرداند که نسبت به کل سند است، مگر اینکه رویداد داخل یک عنصر دارای موقعیت (positioned) رخ دهد که در آن صورت مقدار برگشتی نسبت به گوشه‌ی بالا-چپ آن عنصر دارای موقعیت خواهد بود.

## مقدار

یک مقدار صحیح بر حسب پیکسل برای مختصات y اشاره‌گر موس، در زمانی که رویداد موس رخ داده است.

## نمونه‌ها

```html
<p>برای نمایش مختصات موس، لطفاً روی هر نقطه‌ای از صفحه کلیک کنید.</p>

<div id="d1">
  <span>
    این یک div بدون موقعیت است، بنابراین کلیک روی آن مقادیر layerX/layerY را تقریباً مشابه pageX/PageY برمی‌گرداند.
  </span>
</div>

<div id="d2">
  <span>
    این یک div دارای موقعیت است، بنابراین کلیک روی آن مقادیر layerX/layerY را نسبت به گوشه‌ی بالا-چپ همین عنصر دارای موقعیت برمی‌گرداند. توجه کنید که ویژگی‌های pageX/pageY همچنان موقعیت مطلق در سند را برمی‌گردانند، از جمله اسکرول صفحه.
  </span>

  <span>
    صفحه را بیشتر اسکرول کنید! این یک div دارای موقعیت است، بنابراین کلیک روی آن مقادیر layerX/layerY را نسبت به گوشه‌ی بالا-چپ همین عنصر دارای موقعیت برمی‌گرداند. توجه کنید که ویژگی‌های pageX/pageY همچنان موقعیت مطلق در سند را برمی‌گردانند، از جمله اسکرول صفحه.
  </span>
</div>

<div id="d3">
  <form name="form_coords" id="form1">
    شناسه‌ی عنصر والد: <input type="text" name="parentId" size="7" /><br />
    pageX: <input type="text" name="pageXCoords" size="7" /> pageY:
    <input type="text" name="pageYCoords" size="7" /><br />
    layerX: <input type="text" name="layerXCoords" size="7" /> layerY:
    <input type="text" name="layerYCoords" size="7" />
  </form>
</div>
```

```css
#d1 {
  border: solid blue 1px;
  padding: 20px;
}

#d2 {
  position: absolute;
  top: 180px;
  left: 80%;
  right: auto;
  width: 40%;
  border: solid blue 1px;
  padding: 20px;
}

#d3 {
  position: absolute;
  top: 240px;
  left: 20%;
  width: 50%;
  border: solid blue 1px;
  padding: 10px;
}
```

```js
function showCoords(evt) {
  const form = document.forms.form_coords;
  const parentId = evt.target.parentNode.id;
  form.parentId.value = parentId;
  form.pageXCoords.value = evt.pageX;
  form.pageYCoords.value = evt.pageY;
  form.layerXCoords.value = evt.layerX;
  form.layerYCoords.value = evt.layerY;
}

window.addEventListener("mousedown", showCoords);
```

## مشخصات

_این خاصیت بخشی از هیچ مشخصه‌ای نیست._

## سازگاری مرورگر

{{Compat}}