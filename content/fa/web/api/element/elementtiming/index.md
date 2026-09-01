---
title: "Element: elementTiming property"
short-title: elementTiming
slug: Web/API/Element/elementTiming
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Element.elementTiming
---

{{APIRef("DOM")}}{{SeeCompatTable}}

ویژگی **`elementTiming`** از رابط {{domxref("Element")}} عناصری را که قرار است در API {{domxref("PerformanceElementTiming")}} مشاهده شوند، مشخص می‌کند. ویژگی `elementTiming` مقدار صفت [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) را منعکس می‌کند.

## مقدار

یک رشته.

## مثال‌ها

### ثبت مقدار `elementTiming`

در این مثال، افزودن صفت [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) به عنصر {{HTMLElement("img")}} باعث می‌شود تصویر مورد مشاهده قرار گیرد.

```html
<img
  src="image.jpg"
  alt="a nice image"
  elementtiming="big-image"
  id="myImage" />
```

می‌توانید مقدار رشته‌ایِ صفت HTML یعنی `elementtiming` را با فراخواندن `el.elementTiming` به دست آورید.

```js
const el = document.getElementById("myImage");
console.log(el.elementTiming); // "big-image"
```

برای مثال کامل‌تر در مورد نحوه استفاده از Element Timing API، به {{domxref("PerformanceElementTiming")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceElementTiming")}}
- [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) صفت HTML