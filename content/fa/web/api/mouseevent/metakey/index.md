---
title: "MouseEvent: metaKey property"
short-title: metaKey
slug: Web/API/MouseEvent/metaKey
page-type: web-api-instance-property
browser-compat: api.MouseEvent.metaKey
---

{{APIRef("Pointer Events")}}

ویژگی فقط-خواندنی **`MouseEvent.metaKey`** یک مقدار بولی است که نشان می‌دهد آیا کلید <kbd>meta</kbd> هنگام وقوع یک رویداد ماوس فشرده شده بود یا نه.

توجه داشته باشید که بسیاری از سیستم‌عامل‌ها عملکردهای خاصی را به کلید <kbd>meta</kbd> اختصاص می‌دهند، بنابراین این ویژگی ممکن است حتی زمانی که کلید واقعاً فشرده شده است `false` باشد. برای مثال، در ویندوز این کلید ممکن است منوی استارت را باز کند.

> [!NOTE]
> در صفحه‌کلیدهای مکینتاش، این کلید همان کلید <kbd>command</kbd> (<kbd>⌘</kbd>) است.
> در صفحه‌کلیدهای ویندوز، این کلید کلید ویندوز (<kbd>⊞</kbd>) است.

## مقدار

یک مقدار بولی که `true` نشان‌دهنده فشرده شدن کلید و `false` نشان‌دهنده _فشرده نشدن_ کلید است.

## مثال‌ها

این مثال هنگام فعال‌سازی یک رویداد {{domxref("Element/click_event", "click")}}، ویژگی `metaKey` را ثبت می‌کند.

### HTML

```html
<p>برای آزمایش ویژگی <code>metaKey</code>، هر جایی کلیک کنید.</p>
<p id="log"></p>
```

### JavaScript

```js
let log = document.querySelector("#log");
document.addEventListener("click", logKey);

function logKey(e) {
  log.textContent = `کلید meta فشرده شده است: ${e.metaKey}`;
}
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("MouseEvent") }}