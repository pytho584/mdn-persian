---
title: "MouseEvent: layerX property"
short-title: layerX
slug: Web/API/MouseEvent/layerX
page-type: web-api-instance-property
status:
  - non-standard
browser-compat: api.MouseEvent.layerX
---

{{APIRef("Pointer Events")}}{{Non-standard_Header}}

**ویژگی فقطخواندنیِ `MouseEvent.layerX`** مختصات افقی رویداد را نسبت به «لایهٔ فعلی» برمی‌گرداند.

این ویژگی پیمایش صفحه را در نظر گرفته و مقداری را نسبت به کل سند برمی‌گرداند، مگر اینکه رویداد درون یک عنصر موقعیت‌دار رخ دهد؛ در این صورت، مقدار بازگشتی نسبت به گوشهٔ بالا-چپِ همان عنصر موقعیت‌دار است.

## مقدار

یک مقدار صحیح بر حسب پیکسل که مختصات x اشاره‌گر ماوس را هنگام رخ دادن رویداد ماوس نشان می‌دهد.

## مثال‌ها

```html
<p>To display the mouse coordinates please click anywhere on the page.</p>

<div id="d1">
  <span>
    This is an un-positioned div so clicking it will return layerX/layerY values
    almost the same as pageX/PageY values.
  </span>
</div>

<div id="d2">
  <span>
    This is a positioned div so clicking it will return layerX/layerY values
    that are relative to the top-left corner of this positioned element. Note
    the pageX\pageY properties still return the absolute position in the
    document, including page scrolling.
  </span>

  <span>
    Make the page scroll more! This is a positioned div so clicking it will
    return layerX/layerY values that are relative to the top-left corner of this
    positioned element. Note the pageX\pageY properties still return the
    absolute position in the document, including page scrolling.
  </span>
</div>

<div id="d3">
  <form name="form_coords" id="form1">
    Parent Element id: <input type="text" name="parentId" size="7" /><br />
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

_این ویژگی بخشی از هیچ استانداردی نیست._

## سازگاری مرورگر

{{Compat}}