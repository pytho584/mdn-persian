---
title: "CSSPageRule"
slug: Web/API/CSSPageRule
page-type: web-api-interface
browser-compat: api.CSSPageRule
---

{{APIRef("CSSOM")}}

**`CSSPageRule`** یک قانون CSS {{cssxref("@page")}} را نمایش می‌دهد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از آباء خود {{domxref("CSSGroupingRule")}} و {{domxref("CSSRule")}} به ارث می‌برد._

- {{domxref("CSSPageRule.selectorText")}}
  - : متن انتخابگر صفحه مرتبط با at-rule را نمایش می‌دهد.
- {{domxref("CSSPageRule.style")}} {{ReadOnlyInline}}
  - : بلوک اظهارنامه (declaration block) مرتبط با at-rule را برمی‌گرداند.

## روش‌های نمونه

_روش‌ها را از آباء خود {{domxref("CSSGroupingRule")}} و {{domxref("CSSRule")}} به ارث می‌برد._

## مثال‌ها

### فیلتر کردن برای قوانین صفحه

این مثال نشان می‌دهد که چگونه می‌توانید اشیاء `CSSPageRule` را برای قوانین {{cssxref("@page")}} بارگذاری شده توسط سند پیدا کنید.

```html hidden
<pre id="log"></pre>
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```css hidden
#log {
  height: 220px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### CSS

در زیر، استایل‌هایی برای صفحه با استفاده از یک قانون {{cssxref("@page")}} تعریف می‌کنیم.

```css
@page {
  margin: 1cm;
}
```

#### JavaScript

کد از میان تمام sheets در سند و از میان تمام `cssRules` در هر sheet پیمایش می‌کند و اندیس sheet، تعداد قوانین، و نوع هر شیء قانون را ثبت می‌کند. سپس اشیاء `CSSPageRule` را با استفاده از نوع آن‌ها تشخیص می‌دهیم (با اطلاعات کاری انجام نمی‌دهیم).

```js
for (
  let sheetCount = 0;
  sheetCount < document.styleSheets.length;
  sheetCount++
) {
  const sheet = document.styleSheets[sheetCount].cssRules;
  log(`styleSheet: ${sheetCount}`);

  const myRules = document.styleSheets[sheetCount].cssRules;
  log(`rules: ${myRules.length}`);
  for (const rule of myRules) {
    log(`rule: ${rule}`);
    if (rule instanceof CSSPageRule) {
      // Do something with CSSPageRule
    }
  }
}
```

#### نتایج

نتایج در زیر نشان داده شده است. همانطور که می‌بینید دو sheet وجود دارد که مربوط به این سند اصلی و فریم کد مثال هستند، و هر کدام تعدادی قانون دارند که تنها یکی از آن‌ها `CSSPageRule` ما است.

{{EmbedLiveSample("Filtering for page rules", "100%", "300px")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}