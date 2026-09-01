---
title: "CSSStyleSheet: insertRule() method"
short-title: insertRule()
slug: Web/API/CSSStyleSheet/insertRule
page-type: web-api-instance-method
browser-compat: api.CSSStyleSheet.insertRule
---

{{APIRef("CSSOM")}}

متد **`CSSStyleSheet.insertRule()`** یک [قاعده CSS](/en-US/docs/Web/API/CSSRule) جدید را در [شیوه‌نامه جاری](/en-US/docs/Web/API/CSSStyleSheet) درج می‌کند.

> [!NOTE]
> اگرچه `insertRule()` منحصراً یک متد از {{domxref("CSSStyleSheet")}} است، اما در واقع قاعده را درون `{{domxref("CSSStyleSheet", "", "", "1")}}.cssRules` — یعنی {{domxref("CSSRuleList")}} داخلی آن — درج می‌کند.

## نحو (Syntax)

```js-nolint
insertRule(rule)
insertRule(rule, index)
```

### پارامترها

- `rule`
  - : یک رشته شامل قاعده‌ای که باید درج شود. محتوای لازم برای قاعده درج‌شده به نوع آن بستگی دارد:
    - **برای [مجموعه‌قاعده‌ها](/en-US/docs/Web/CSS/Guides/Syntax/Introduction#css_statements)**، هم یک [انتخاب‌گر](/en-US/docs/Learn_web_development/Core/Styling_basics/Basic_selectors) و هم یک اعلان سبک.
    - **برای [قواعد at](/en-US/docs/Web/CSS/Guides/Syntax/At-rules)**، هم یک شناسه at و هم محتوای قاعده.
- `index` {{optional_inline}}
  - : یک عدد صحیح مثبت کوچک‌تر یا مساوی با `stylesheet.cssRules.length` که موقعیت قاعده تازه درج‌شده را درون `{{domxref("CSSStyleSheet", "", "", "1")}}.cssRules` نشان می‌دهد. مقدار پیش‌فرض `0` است. (در پیاده‌سازی‌های قدیمی‌تر، این پارامتر اجباری بود. برای جزئیات به [سازگاری مرورگر](#browser_compatibility) مراجعه کنید.)

### مقدار بازگشتی

شاخص قاعده تازه درج‌شده در فهرست قواعد شیوه‌نامه.

### استثناها

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر `index` > `{{domxref("CSSRuleList", "", "", "1")}}.length` باشد، پرتاب می‌شود.
- `HierarchyRequestError` {{domxref("DOMException")}}
  - : اگر `rule` به دلیل محدودیت CSS در شاخص مشخص‌شده قابل درج نباشد، پرتاب می‌شود؛ برای مثال: تلاش برای درج یک قاعده at {{cssxref("@import")}} پس از یک قاعده سبک.
- `SyntaxError` {{domxref("DOMException")}}
  - : اگر بیش از یک قاعده در پارامتر `rule` داده شود، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر `rule` برابر با {{cssxref("@namespace")}} باشد و [فهرست قواعد](/en-US/docs/Web/CSS/Reference/Values/rule-list) شامل قواعد at غیر از `@import` و `@namespace` باشد، پرتاب می‌شود.

## مثال‌ها

### درج یک قاعده جدید

این قطعه کد یک قاعده جدید را به بالای شیوه‌نامه من اضافه می‌کند.

```js
myStyle.insertRule("#blanc { color: white }", 0);
```

### تابعی برای افزودن یک قاعده شیوه‌نامه

```js
/**
 * Add a stylesheet rule to the document (it may be better practice
 * to dynamically change classes, so style information can be kept in
 * genuine stylesheets and avoid adding extra elements to the DOM).
 * Note that an array is needed for declarations and rules since ECMAScript does
 * not guarantee a predictable object iteration order, and since CSS is
 * order-dependent.
 * @param {Array} rules Accepts an array of JSON-encoded declarations
 * @example
addStylesheetRules([
  ['h2', // Also accepts a second argument as an array of arrays instead
    ['color', 'red'],
    ['background-color', 'green', true] // 'true' for !important rules
  ],
  ['.myClass',
    ['background-color', 'yellow']
  ]
]);
*/
function addStylesheetRules(rules) {
  const styleEl = document.createElement("style");

  // Append <style> element to <head>
  document.head.appendChild(styleEl);

  // Grab style element's sheet
  const styleSheet = styleEl.sheet;

  for (let rule of rules) {
    let i = 1,
      selector = rule[0],
      propStr = "";
    // If the second argument of a rule is an array of arrays, correct our variables.
    if (Array.isArray(rule[1][0])) {
      rule = rule[1];
      i = 0;
    }

    for (; i < rule.length; i++) {
      const prop = rule[i];
      propStr += `${prop[0]}: ${prop[1]}${prop[2] ? " !important" : ""};\n`;
    }

    // Insert CSS Rule
    styleSheet.insertRule(
      `${selector}{${propStr}}`,
      styleSheet.cssRules.length,
    );
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSStyleSheet.deleteRule")}}
- [شیوه‌نامه‌های قابل ساخت](https://web.dev/articles/constructable-stylesheets) (web.dev)