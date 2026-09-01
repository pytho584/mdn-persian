---
title: "HTMLTableElement: createCaption() method"
---

---
title: "HTMLTableElement: createCaption() method"
short-title: createCaption()
slug: Web/API/HTMLTableElement/createCaption
page-type: web-api-instance-method
browser-compat: api.HTMLTableElement.createCaption
---

{{APIRef("HTML DOM")}}

متد **`HTMLTableElement.createCaption()`** عنصر {{HtmlElement("caption")}} مرتبط با یک {{HtmlElement("table")}} مشخص را برمی‌گرداند. اگر هیچ عنصر `<caption>` روی جدول وجود نداشته باشد، این متد آن را ایجاد کرده و سپس برمی‌گرداند.

> [!NOTE]
> اگر عنوان وجود نداشته باشد، `createCaption()` یک عنوان جدید را مستقیماً در جدول درج می‌کند. برخلاف حالتی که در آن برای ایجاد عنصر `<caption>` جدید از {{domxref("Document.createElement()")}} استفاده شود، در اینجا نیازی به افزودن جداگانه‌ی عنوان نیست.

## سینتکس

```js-nolint
createCaption()
```

### پارامترها

هیچ.

### مقدار بازگشتی

{{domxref("HTMLTableCaptionElement")}}

## مثال‌ها

این مثال از JavaScript برای افزودن عنوان (Caption) به جدولی که در ابتدا عنوان ندارد، استفاده می‌کند.

### HTML

```html
<table>
  <tbody>
    <tr>
      <td>Cell 1.1</td>
      <td>Cell 1.2</td>
      <td>Cell 1.3</td>
    </tr>
    <tr>
      <td>Cell 2.1</td>
      <td>Cell 2.2</td>
      <td>Cell 2.3</td>
    </tr>
  </tbody>
</table>
```

### JavaScript

```js
let table = document.querySelector("table");
let caption = table.createCaption();
caption.textContent = "This caption was created by JavaScript!";
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}