---
title: "MouseEvent: altKey property"
short-title: altKey
slug: Web/API/MouseEvent/altKey
page-type: web-api-instance-property
browser-compat: api.MouseEvent.altKey
---

{{APIRef("UI Events")}}

ویژگی فقط‌خواندنی **`MouseEvent.altKey`** یک مقدار بولی است که نشان می‌دهد آیا کلید <kbd>alt</kbd> هنگام وقوع یک رویداد ماوس معین فشرده شده است یا نه.

توجه داشته باشید که مرورگر همیشه نمی‌تواند کلید <kbd>alt</kbd> را در برخی سیستم‌عامل‌ها تشخیص دهد. به‌عنوان مثال، در برخی از توزیع‌های لینوکس، کلیک چپ ماوس همراه با کلید <kbd>alt</kbd> برای جابه‌جایی یا تغییر اندازه پنجره‌ها استفاده می‌شود.

> [!NOTE]
> در صفحه‌کلیدهای مکینتاش، این کلید با نام کلید <kbd>option</kbd> نیز شناخته می‌شود.

## مقدار

یک مقدار بولی، که در آن `true` نشان می‌دهد که کلید فشرده شده است و `false` نشان می‌دهد که کلید _فشرده نشده_ است.

## مثال‌ها

این مثال هنگام فعال‌کردن رویداد {{domxref("Element/click_event", "click")}} ویژگی `altKey` را ثبت می‌کند.

### HTML

```html
<p>Click anywhere to test the <code>altKey</code> property.</p>
<p id="log"></p>
```

### JavaScript

```js
let log = document.querySelector("#log");
document.addEventListener("click", logKey);

function logKey(e) {
  log.textContent = `The alt key is pressed: ${e.altKey}`;
}
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("MouseEvent") }}