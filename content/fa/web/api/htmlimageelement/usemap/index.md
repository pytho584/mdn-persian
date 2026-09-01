---
title: "HTMLImageElement: useMap property"
---

---
title: "HTMLImageElement: useMap property"
short-title: useMap
slug: Web/API/HTMLImageElement/useMap
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.useMap
---

{{APIRef("HTML DOM")}}

ویژگی **`useMap`** از رابط {{domxref("HTMLImageElement")}} نامِ نقشهٔ تصویر سمت کلاینت را که باید روی تصویر اعمال شود، فراهم می‌کند. این ویژگی، ویژگیِ محتوایی [`usemap`](/en-US/docs/Web/HTML/Reference/Elements/img#usemap) عنصر `<img>` را منعکس می‌کند.

## مقدار

یک رشته (string) شامل نماد هش `#` و سپس [`name`](/en-US/docs/Web/HTML/Reference/Elements/map#name) عنصر {{HTMLElement("map")}} که نقشهٔ تصویریِ اعمال‌شده روی تصویر را تعریف می‌کند.

## مثال‌ها

### استفاده از useMap

یک `<map>` با این مشخصات را در نظر بگیرید:

```html
<map name="mainmenu-map">
  <area
    shape="circle"
    coords="25, 25, 75"
    href="/index.html"
    alt="Return to home page" />
  <area shape="rect" coords="25, 25, 100, 150" href="/index.html" alt="Shop" />
</map>
```

با توجه به نقشهٔ تصویری به نام `mainmenu-map`، می‌توانید تصاویری را به‌صورت پویا بسازید که به این نقشهٔ تصویری ارجاع می‌دهند:

```js
const image = new Image();
image.src = "menu-box.png";
image.alt = "";
image.useMap = "#mainmenu-map";
```

برای مثال‌های بیشتر (از جمله مثال‌های تعاملی)، مقاله‌های مربوط به عناصر {{HTMLElement("map")}} و {{HTMLElement("area")}} و همچنین [راهنمای استفاده از نقشه‌های تصویری](/en-US/docs/Web/HTML/How_to/Add_a_hit_map_on_top_of_an_image) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [افزودن hitmap روی تصویر](/en-US/docs/Web/HTML/How_to/Add_a_hit_map_on_top_of_an_image)
- {{HTMLElement("map")}}
- {{HTMLElement("area")}}