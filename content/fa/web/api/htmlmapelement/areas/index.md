---
title: "HTMLMapElement: areas property"
short-title: areas
slug: Web/API/HTMLMapElement/areas
page-type: web-api-instance-property
browser-compat: api.HTMLMapElement.areas
---

{{ApiRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`areas`** از رابط {{domxref("HTMLMapElement")}} مجموعه‌ای از عناصر {{HTMLElement("area")}} مرتبط با عنصر {{HTMLElement("map")}} را بازمی‌گرداند.

## مقدار

یک شیء {{domxref("HTMLCollection")}} متشکل از عناصر {{domxref("HTMLAreaElement")}}.

## مثال

```html
<map id="image-map" name="image-map">
  <area shape="circle" coords="50,50,35" href="#left" alt="left arrow" />
  <area shape="circle" coords="150,50,35" href="#right" alt="right arrow" />
</map>
<img
  usemap="#image-map"
  src="left-right-arrow.png"
  alt="left right arrow image" />
<output></output>
```

```css hidden
output {
  display: block;
}
```

```js
const mapElement = document.getElementById("image-map");
const outputElement = document.querySelector("output");

for (const area of mapElement.areas) {
  area.addEventListener("click", (event) => {
    outputElement.textContent = `You clicked on the ${area.alt} area.\n\n`;
  });
}
```

### نتیجه

{{EmbedLiveSample("Example",100,150)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLAreaElement")}}
- {{domxref("HTMLImageElement.useMap")}}