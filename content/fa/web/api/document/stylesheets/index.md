---
title: "Document: styleSheets property"
short-title: styleSheets
slug: Web/API/Document/styleSheets
page-type: web-api-instance-property
browser-compat: api.Document.styleSheets
---

{{APIRef("CSSOM")}}

ویژگی فقط‌خواندنی **`styleSheets`** در رابط {{domxref("Document")}}، یک {{domxref('StyleSheetList')}} از اشیاء {{domxref('CSSStyleSheet')}} را برای برگه‌های سبکی که به‌طور صریح در یک سند لینک شده یا جاسازی شده‌اند، برمی‌گرداند.

## مقدار

فهرست بازگشتی به ترتیب زیر مرتب می‌شود:

- برگه‌های سبکی دریافت‌شده از سرآیندهای {{HTTPHeader("Link")}} ابتدا قرار می‌گیرند و بر اساس ترتیب سرآیند مرتب می‌شوند.
- برگه‌های سبکی دریافت‌شده از DOM پس از آن‌ها قرار می‌گیرند و بر اساس [ترتیب درخت](https://dom.spec.whatwg.org/#concept-tree-order) مرتب می‌شوند.

## مثال‌ها

### بازیابی یک برگه سبک خاص با عنوان آن

```js
function getStyleSheet(uniqueTitle) {
  for (const sheet of document.styleSheets) {
    if (sheet.title === uniqueTitle) {
      return sheet;
    }
  }
}
```

### دسترسی به قوانین درون برگه سبک

با استفاده از اشیاء stylesheet، style و {{domxref("CSSRule")}} می‌توانید به این برگه‌های سبک و قوانین آن‌ها به‌صورت جداگانه دسترسی پیدا کنید؛ همان‌طور که در این مثال نشان داده شده است که همهٔ انتخاب‌گرهای قوانین سبک را در کنسول چاپ می‌کند.

```js
for (const styleSheet of document.styleSheets) {
  for (const rule of styleSheet.cssRules) {
    console.log(`${rule.selectorText}\n`);
  }
}
```

برای سندی که فقط یک برگه سبک دارد و سه قانون زیر در آن تعریف شده است:

```css
body {
  background-color: darkblue;
}
p {
  font-family: "Arial";
  font-size: 10pt;
  margin-left: 0.125in;
}
#lumpy {
  display: none;
}
```

این اسکریپت خروجی زیر را تولید می‌کند:

```plain
BODY
P
#LUMPY
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}