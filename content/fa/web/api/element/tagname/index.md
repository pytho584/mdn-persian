---
title: "Element: tagName property"
short-title: tagName
slug: Web/API/Element/tagName
page-type: web-api-instance-property
browser-compat: api.Element.tagName
---

{{ApiRef("DOM")}}

ویژگی فقط‌خواندنی **`tagName`** از رابط {{domxref("Element")}} نام تگ عنصری را که روی آن فراخوانی می‌شود برمی‌گرداند.

به‌عنوان مثال، اگر عنصر یک {{HTMLElement("img")}} باشد، ویژگی `tagName` آن `IMG` است (برای اسناد HTML؛ ممکن است برای اسناد XML/XHTML حروف بزرگ و کوچک متفاوت باشد). نکته: می‌توانید از ویژگی {{domxref("Element.localName", "localName")}} برای دسترسی به نام محلی عنصر استفاده کنید — که در مثال بالا `img` (با حروف کوچک) است.

## مقدار

رشته‌ای که نام تگ عنصر را نشان می‌دهد. حروف بزرگ/کوچک این رشته به نوع سند بستگی دارد:

- برای درخت‌های DOM که اسناد HTML را نمایش می‌دهند، نام تگ برگردانده‌شده همیشه به شکل متعارف با حروف بزرگ است. برای مثال، `tagName` روی یک عنصر {{HTMLElement("div")}} مقدار `"DIV"` را برمی‌گرداند.
- نام تگ عناصر در درخت DOM نوع XML در همان حروفی که در فایل XML اصلی نوشته شده‌اند برگردانده می‌شود. اگر یک سند XML شامل تگ `"<SomeTag>"` باشد، مقدار ویژگی `tagName` برابر `"SomeTag"` خواهد بود.

برای اشیاء {{domxref("Element")}}، مقدار `tagName` همان مقدار ویژگی {{domxref("Node.nodeName", "nodeName")}} است که شیء عنصر از {{domxref("Node")}} به ارث می‌برد.

## مثال‌ها

### HTML

```html
<span id="born">When I was born…</span>
```

### JavaScript

```js
const span = document.getElementById("born");
console.log(span.tagName);
```

در XHTML (یا هر قالب XML دیگری)، حروف اصلی حفظ می‌شود، بنابراین اگر نام تگ اصلی با حروف کوچک ساخته شده باشد، `"span"` خروجی داده می‌شود. در HTML، بدون توجه به حروفی که هنگام ایجاد سند اصلی استفاده شده، `"SPAN"` خروجی داده می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.localName")}}