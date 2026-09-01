---
title: "Element: computedStyleMap() method"
short-title: computedStyleMap()
slug: Web/API/Element/computedStyleMap
page-type: web-api-instance-method
browser-compat: api.Element.computedStyleMap
---

{{APIRef("CSS Typed Object Model API")}}

متد **`computedStyleMap()`** در رابط {{domxref("Element")}} یک {{domxref("StylePropertyMapReadOnly")}} برمی‌گرداند که بازنمایی فقط‌خواندنی از یک بلوک اعلان CSS ارائه می‌دهد و جایگزینی برای {{domxref("CSSStyleDeclaration")}} است.

## سینتکس

```js-nolint
computedStyleMap()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک شیء {{domxref("StylePropertyMapReadOnly")}}.

برخلاف {{domxref("Window.getComputedStyle")}}، مقدار بازگشتی شامل [مقدار محاسبه‌شده](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#computed_value) است، نه [مقدار حل‌شده](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#resolved_value). برای بیشتر ویژگی‌ها این دو یکسان هستند، به‌جز چند ویژگی مرتبط با چیدمان که در آن‌ها مقدار حل‌شده به جای مقدار محاسبه‌شده، [مقدار استفاده‌شده](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#used_value) است. برای جزئیات بیشتر به مثال [مقایسه با `getComputedStyle()`](#comparison_with_getcomputedstyle) مراجعه کنید.

## مثال‌ها

### دریافت سبک‌های پیش‌فرض

ما با کمی HTML ساده شروع می‌کنیم: یک پاراگراف حاوی یک پیوند، و یک فهرست تعریف که همهٔ جفت‌های ویژگی/مقدار CSS را به آن اضافه خواهیم کرد.

```html
<p>
  <a href="https://example.com">Link</a>
</p>
<dl id="regurgitation"></dl>
```

کمی CSS اضافه می‌کنیم:

```css
a {
  --color: red;
  color: var(--color);
}
```

جاوااسکریپتی اضافه می‌کنیم تا پیوند را بگیرد و با استفاده از `computedStyleMap()` فهرستی از همهٔ مقادیر ویژگی‌های CSS را به‌صورت یک فهرست تعریف برگرداند.

```js
// get the element
const myElement = document.querySelector("a");

// get the <dl> we'll be populating
const stylesList = document.querySelector("#regurgitation");

// Retrieve all computed styles with computedStyleMap()
const allComputedStyles = myElement.computedStyleMap();

// iterate through the map of all the properties and values, adding a <dt> and <dd> for each
for (const [prop, val] of allComputedStyles) {
  // properties
  const cssProperty = document.createElement("dt");
  cssProperty.appendChild(document.createTextNode(prop));
  stylesList.appendChild(cssProperty);

  // values
  const cssValue = document.createElement("dd");
  cssValue.appendChild(document.createTextNode(val));
  stylesList.appendChild(cssValue);
}
```

در [مرورگرهایی که از `computedStyleMap()` پشتیبانی می‌کنند](#browser_compatibility)، فهرستی از همهٔ ویژگی‌ها و مقادیر CSS خواهید دید. در سایر مرورگرها فقط یک پیوند می‌بینید.

{{EmbedLiveSample("getting_default_styles", 300, 300)}}

آیا تا به حال متوجه شده‌اید که یک پیوند چند ویژگی پیش‌فرض CSS دارد؟ عبارت `document.querySelector("a")` را به `document.querySelector("p")` تغییر دهید و متوجه تفاوت در مقادیر محاسبه‌شدهٔ پیش‌فرض `margin-top` و `margin-bottom` خواهید شد.

### مقایسه با getComputedStyle()

{{domxref("Window.getComputedStyle()")}} [مقدار حل‌شده](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#resolved_value) را برمی‌گرداند، در حالی که `computedStyleMap()` [مقدار محاسبه‌شده](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#computed_value) را برمی‌گرداند. این دو معمولاً یکسان هستند، اما برای برخی ویژگی‌ها، مقدار حل‌شده به جای مقدار محاسبه‌شده، [مقدار استفاده‌شده](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#used_value) است. برای مثال، مقادیر درصدی عرض‌ها پس از چیدمان به مقادیر پیکسلی تبدیل می‌شوند، بنابراین مقدار استفاده‌شده بر حسب پیکسل است، در حالی که مقدار محاسبه‌شده همچنان درصدی است.

توجه داشته باشید که شیوهٔ ارائهٔ ما باعث می‌شود این دو API شبیه‌تر از آنچه هستند به نظر برسند. `computedStyleMap()` شامل اشیاء [CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API) است، در حالی که `getComputedStyle()` شامل رشته‌هاست. اولی اطلاعات یکسان را به شکلی ساختاریافته‌تر و قابل پردازش‌تر ارائه می‌دهد.

در این مثال، ویژگی `width` به‌صورت درصد مشخص شده است، بنابراین مقدار محاسبه‌شده به‌صورت درصد داده می‌شود، اما مقدار حل‌شده بر حسب پیکسل داده می‌شود. `height` همواره بر حسب پیکسل است. `background-color` یک رنگ نام‌گذاری‌شده است، اما به یک مقدار RGB محاسبه می‌شود.

```html
<div class="container">
  <div class="item"></div>
</div>
<pre id="result"></pre>
```

```css
.container {
  width: 200px;
  height: 200px;
}

.item {
  width: 50%;
  height: 100px;
  background-color: tomato;
}
```

```js
const item = document.querySelector(".item");
const result = document.querySelector("#result");
const resolvedValues = getComputedStyle(item);
const computedValues = item.computedStyleMap();

result.textContent = `resolvedValues.width = ${resolvedValues.width}
computedValues.get("width") = ${computedValues.get("width")}

resolvedValues.height = ${resolvedValues.height}
computedValues.get("height") = ${computedValues.get("height")}

resolvedValues.backgroundColor = ${resolvedValues.backgroundColor}
computedValues.get("background-color") = ${computedValues.get(
  "background-color",
)}`;
```

{{EmbedLiveSample("comparison_with_getcomputedstyle", "", 350)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("Window.getComputedStyle()")}}