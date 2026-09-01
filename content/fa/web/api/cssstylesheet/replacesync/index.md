---
title: "CSSStyleSheet: replaceSync() method"
---

---
title: "CSSStyleSheet: replaceSync() method"
short-title: replaceSync()
slug: Web/API/CSSStyleSheet/replaceSync
page-type: web-api-instance-method
browser-compat: api.CSSStyleSheet.replaceSync
---

{{APIRef("CSSOM")}}

متد **`replaceSync()`** از واسط {{domxref("CSSStyleSheet")}} به‌صورت همزمان محتوای شیوه‌نامه را با محتوای ارسال‌شده به آن جایگزین می‌کند.

متدهای `replaceSync()` و {{domxref("CSSStyleSheet.replace()")}} فقط روی شیوه‌نامه‌ای قابل استفاده هستند که با سازندهٔ {{domxref("CSSStyleSheet.CSSStyleSheet()","CSStyleSheet()")}} ایجاد شده باشد.

## Syntax

```js-nolint
replaceSync(text)
```

### Parameters

- `text`
  - : رشته‌ای شامل قواعد سبک که محتوای شیوه‌نامه را جایگزین می‌کند. اگر رشته حاوی فهرست قابل تجزیهٔ قواعد نباشد، مقدار به یک رشتهٔ خالی تنظیم می‌شود.

    > [!NOTE]
    > اگر هر یک از قواعد ارسال‌شده در `text` یک شیوه‌نامهٔ خارجی واردشده با قاعدهٔ {{cssxref("@import")}} باشد، آن قواعد حذف و یک هشدار در کنسول چاپ می‌شود.

### Return value

هیچ (`undefined`).

### Exceptions

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر شیوه‌نامه با استفاده از سازندهٔ {{domxref("CSSStyleSheet.CSSStyleSheet()","CSStyleSheet()")}} ایجاد نشده باشد یا اگر شیوه‌نامه به‌عنوان غیرقابل‌تغییر علامت‌گذاری شده باشد، پرتاب می‌شود.

## Examples

در مثال زیر، یک شیوه‌نامهٔ جدید ایجاد شده و دو قاعدهٔ CSS با استفاده از `replaceSync` اضافه می‌شود.

```js
const stylesheet = new CSSStyleSheet();

stylesheet.replaceSync("body { font-size: 1.4em; } p { color: red; }");
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Constructable Stylesheets](https://web.dev/articles/constructable-stylesheets) (web.dev)
- [Using the Shadow DOM](/en-US/docs/Web/API/Web_components/Using_shadow_DOM)