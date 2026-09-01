---
title: "Element: getAttributeNS() method"
short-title: getAttributeNS()
slug: Web/API/Element/getAttributeNS
page-type: web-api-instance-method
browser-compat: api.Element.getAttributeNS
---

{{APIRef("DOM")}}

متد **`getAttributeNS()`** در رابط {{domxref("Element")}} مقدار رشته‌ای ویژگی (attribute) با فضای نام (namespace) و نام مشخص‌شده را برمی‌گرداند. اگر ویژگی نام‌برده وجود نداشته باشد، مقدار بازگشتی یا `null` خواهد بود یا `""` (رشتهٔ خالی)؛ برای جزئیات به [یادداشت‌ها](#notes) مراجعه کنید.

اگر با اسناد HTML کار می‌کنید و نیازی به مشخص کردن فضای نام خاصی برای ویژگی مورد نظر ندارید، به‌جای آن از متد {{domxref("Element.getAttribute()", "getAttribute()")}} استفاده کنید.

## نحو (Syntax)

```js-nolint
getAttributeNS(namespace, name)
```

### پارامترها

- `namespace`
  - : فضای نامی که باید ویژگی مشخص‌شده در آن جستجو شود.
- `name`
  - : نام ویژگی که باید جستجو شود.

### مقدار بازگشتی

مقدار رشته‌ای ویژگی مشخص‌شده. اگر ویژگی وجود نداشته باشد، نتیجه `null` است.

> [!NOTE]
> نسخه‌های اولیهٔ مشخصات DOM این متد را به‌گونه‌ای توصیف کرده بودند که برای ویژگی‌های ناموجود یک رشتهٔ خالی返回 کند، اما معمولاً به این صورت پیاده‌سازی نمی‌شد زیرا `null` منطقی‌تر است. مشخصات DOM4 اکنون بیان می‌کند که این متد باید برای ویژگی‌های ناموجود `null` بازگرداند.

## مثال‌ها

سند SVG زیر مقدار ویژگی `foo` را در یک فضای نام سفارشی می‌خواند.

```xml
<svg xmlns="http://www.w3.org/2000/svg"
    xmlns:test="http://www.example.com/2014/test" width="40" height="40">

  <circle id="target" cx="12" cy="12" r="10" stroke="#444444"
      stroke-width="2" fill="none" test:foo="Hello namespaced attribute!"/>

  <script>
    const ns = 'http://www.example.com/2014/test';
    const circle = document.getElementById('target');

    console.log(`attribute test:foo: "${circle.getAttributeNS(ns, 'foo')}"`);
  </script>
</svg>
```

در یک سند HTML، ویژگی باید با `test:foo` قابل دسترسی باشد زیرا فضای نام پشتیبانی نمی‌شود.

```html
<svg
  xmlns="http://www.w3.org/2000/svg"
  xmlns:test="http://www.example.com/2014/test"
  width="40"
  height="40">
  <circle
    id="target"
    cx="12"
    cy="12"
    r="10"
    stroke="#444444"
    stroke-width="2"
    fill="none"
    test:foo="Foo value" />
</svg>
```

```js
const ns = "http://www.example.com/2014/test";
const circle = document.getElementById("target");
console.log(`Attribute value: ${circle.getAttribute("test:foo")}`);
```

## یادداشت‌ها

`getAttributeNS()` با {{domxref("element.getAttribute()", "getAttribute()")}} تفاوت دارد از این جهت که به شما امکان می‌دهد ویژگی مورد نظر را به‌عنوان بخشی از یک فضای نام خاص مشخص کنید، همان‌طور که در مثال بالا مشاهده می‌کنید، جایی که ویژگی بخشی از فضای نام فرضی «test» است.

پیش از مشخصات DOM4، این متد به‌گونه‌ای تعریف شده بود که برای ویژگی‌های ناموجود به‌جای null یک رشتهٔ خالی بازگرداند. با این حال، بیشتر مرورگرها در عوض null برمی‌گرداندند. از DOM4 به بعد، مشخصات اکنون می‌گوید که باید null بازگردانده شود. با این حال، برخی مرورگرهای قدیمی‌تر یک رشتهٔ خالی برمی‌گردانند. به همین دلیل، اگر احتمال می‌دهید که ویژگی مورد نظر روی عنصر مشخص‌شده وجود نداشته باشد، بهتر است پیش از فراخوانی `getAttributeNS()` از {{domxref("element.hasAttributeNS()", "hasAttributeNS()")}} برای بررسی وجود ویژگی استفاده کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.hasAttributeNS()")}}
- {{domxref("Element.setAttributeNS()")}}
- {{domxref("Element.removeAttributeNS()")}}