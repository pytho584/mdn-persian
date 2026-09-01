---
title: "CSSStyleSheet: CSSStyleSheet() constructor"
short-title: CSSStyleSheet()
slug: Web/API/CSSStyleSheet/CSSStyleSheet
page-type: web-api-constructor
browser-compat: api.CSSStyleSheet.CSSStyleSheet
---

{{APIRef("CSSOM")}}

سازندهٔ **`CSSStyleSheet()`** یک شیء جدید {{domxref("CSSStyleSheet")}} می‌سازد که به‌عنوان یک [استایل‌شیت](/en-US/docs/Glossary/Style_sheet) واحد در نظر گرفته می‌شود.

پس از ساخته‌شدن استایل‌شیت، می‌توان از متدهای {{domxref("CSSStyleSheet.replace()")}}، {{domxref("CSSStyleSheet.replaceSync()")}}، {{domxref("CSSStyleSheet.insertRule()")}} و {{domxref("CSSStyleSheet.deleteRule()")}} برای تغییر قواعد (rules) استایل‌شیت جدید استفاده کرد.

به استایل‌شیتی که با استفاده از این متد ساخته می‌شود، «استایل‌شیت ساخته‌شده» (constructed stylesheet) گفته می‌شود. یک استایل‌شیت ساخته‌شده را می‌توان با استفاده از {{domxref("ShadowRoot.adoptedStyleSheets")}} و {{domxref("Document.adoptedStyleSheets")}} بین یک سند و زیردرخت‌های shadow DOM آن به اشتراک گذاشت.

## سینتکس

```js-nolint
new CSSStyleSheet()
new CSSStyleSheet(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء شامل موارد زیر:
    - `baseURL` {{optional_inline}}
      - : رشته‌ای حاوی `baseURL` که برای حل‌کردن (resolve) آدرس‌های نسبی در استایل‌شیت استفاده می‌شود.
    - `media` {{optional_inline}}
      - : یک {{domxref("MediaList")}} که شامل فهرستی از قواعد رسانه‌ای است، یا رشته‌ای که شامل یک قاعدهٔ واحد است.
    - `disabled` {{optional_inline}}
      - : یک {{jsxref("Boolean")}} که مشخص می‌کند آیا استایل‌شیت غیرفعال است یا نه. به‌طور پیش‌فرض `false` است.

## مثال‌ها

در مثال زیر، یک {{domxref("CSSStyleSheet")}} جدید با قاعدهٔ رسانه‌ای `"print"` ساخته می‌شود. چاپ {{domxref("StyleSheet.media")}} در کنسول، یک {{domxref("MediaList")}} با یک ورودی برای این قاعدهٔ چاپ برمی‌گرداند.

```js
let stylesheet = new CSSStyleSheet({ media: "print" });
console.log(stylesheet.media);
```

### به اشتراک‌گذاشتن استایل‌شیت‌ها با shadow DOM

کد زیر نشان می‌دهد که استایل‌شیت ساخته می‌شود و سپس {{domxref("CSSStyleSheet.replaceSync()")}} برای افزودن یک قاعده به استایل‌شیت فراخوانی می‌شود.

```js
// Create an empty "constructed" stylesheet
const sheet = new CSSStyleSheet();
// Apply a rule to the sheet
sheet.replaceSync("a { color: red; }");
```

سپس یک {{domxref("ShadowRoot")}} ساخته و شیء استایل‌شیت را در یک آرایه به ویژگی {{domxref("ShadowRoot.adoptedStyleSheets")}} پاس می‌دهیم.

```js
// Create an element in the document and then create a shadow root:
const node = document.createElement("div");
const shadow = node.attachShadow({ mode: "open" });

// Adopt the sheet into the shadow DOM
shadow.adoptedStyleSheets = [sheet];
```

پس از اضافه‌شدن استایل‌شیت‌ها به آرایه، می‌توان آن‌ها را تغییر داد. در ادامه، یک قاعدهٔ جدید را با استفاده از {{domxref("CSSStyleSheet.insertRule()")}} به همان استایل‌شیت اضافه می‌کنیم.

```js
sheet.insertRule("* { background-color: blue; }");
// The document will now have blue background.
```

همان استایل‌شیت را می‌توان با چندین زیردرخت shadow در همان سند به اشتراک گذاشت. برای مثال‌های بیشتر، {{domxref("ShadowRoot.adoptedStyleSheets")}} را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.adoptedStyleSheets")}}
- [Constructable Stylesheets](https://web.dev/articles/constructable-stylesheets) (web.dev)
- [استفاده از Shadow DOM](/en-US/docs/Web/API/Web_components/Using_shadow_DOM)
- [construct-style-sheets-polyfill](https://www.npmjs.com/package/construct-style-sheets-polyfill)