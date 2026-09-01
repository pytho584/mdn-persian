---
title: "CSSStyleSheet: replace() method"
short-title: replace()
slug: Web/API/CSSStyleSheet/replace
page-type: web-api-instance-method
browser-compat: api.CSSStyleSheet.replace
---

{{APIRef("CSSOM")}}

متد **`replace()`** از رابط {{domxref("CSSStyleSheet")}} به‌صورت ناهمگام (asynchronous) محتوای شیوه‌نامه را با محتوایی که به آن داده شده جایگزین می‌کند. این متد یک وعده (Promise) برمی‌گرداند که با شیء `CSSStyleSheet` حل می‌شود.

متدهای `replace()` و {{domxref("CSSStyleSheet.replaceSync()")}} فقط روی شیوه‌نامه‌ای قابل استفاده هستند که با سازنده {{domxref("CSSStyleSheet.CSSStyleSheet()","CSSStyleSheet()")}} ایجاد شده باشد.

## نحو (Syntax)

```js-nolint
replace(text)
```

### پارامترها

- `text`
  - : یک رشته شامل قوانین سبک (style rules) که باید جایگزین محتوای شیوه‌نامه شود. اگر رشته شامل فهرست قابل تجزیه‌ای از قوانین نباشد، مقدار به یک رشته خالی تنظیم می‌شود.

    > [!NOTE]
    > اگر هر یک از قوانین ارسال‌شده در `text` یک شیوه‌نامه خارجی واردشده با قانون {{cssxref("@import")}} باشد، آن قوانین حذف شده و یک هشدار در کنسول چاپ می‌شود.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با {{domxref("CSSStyleSheet")}} حل می‌شود.

### استثناها (Exceptions)

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر یکی از این دو شرط برقرار باشد پرتاب می‌شود:
    - شیوه‌نامه با استفاده از سازنده {{domxref("CSSStyleSheet.CSSStyleSheet()","CSSStyleSheet()")}} ایجاد نشده باشد.
    - شیوه‌نامه به‌عنوان غیرقابل تغییر علامت‌گذاری شده باشد.

## مثال‌ها

در مثال زیر، یک شیوه‌نامه جدید ایجاد می‌شود و دو قانون CSS با استفاده از `replace()` اضافه می‌شود. سپس اولین قانون در کنسول چاپ می‌شود که نتیجه آن خواهد بود: `body { font-size: 1.4em; }`

```js
const stylesheet = new CSSStyleSheet();

stylesheet
  .replace("body { font-size: 1.4em; } p { color: red; }")
  .then(() => {
    console.log(stylesheet.cssRules[0].cssText);
  })
  .catch((err) => {
    console.error("Failed to replace styles:", err);
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [شیوه‌نامه‌های قابل ساخت (Constructable Stylesheets)](https://web.dev/articles/constructable-stylesheets) (web.dev)
- [استفاده از Shadow DOM](/en-US/docs/Web/API/Web_components/Using_shadow_DOM)