---
title: "NamedNodeMap: setNamedItem() method"

---

---
title: "NamedNodeMap: setNamedItem() method"
short-title: setNamedItem()
slug: Web/API/NamedNodeMap/setNamedItem
page-type: web-api-instance-method
browser-compat: api.NamedNodeMap.setNamedItem
---

{{APIRef("DOM")}}

متد **`setNamedItem()`** از رابط {{domxref("NamedNodeMap")}}،
ویژگی {{domxref("Attr")}} مشخص‌شده با نام آن را در نقشه قرار می‌دهد.
اگر قبلاً یک {{domxref("Attr")}} با همان نام در نقشه وجود داشته باشد،
_جایگزین_ می‌شود.

## نحو

```js-nolint
setNamedItem(attr)
```

### پارامترها

- `attr`
  - : ویژگی‌ای که باید در نقشه درج شود.

### مقدار بازگشتی

در صورت جایگزینی، ویژگی قدیمی را برمی‌گرداند، و اگر ویژگی جدید باشد، `null` را برمی‌گرداند.

### استثناها

- `InUseAttributeError` {{domxref("DOMException")}}
  - : اگر ویژگی هنوز بخشی از نقشه دیگری باشد، پرتاب می‌شود.

## مثال

```html
<span class="foo" id="bar"></span>
<pre contenteditable></pre>
```

```js
const span = document.querySelector("span");
const pre = document.querySelector("pre");

let result = `عنصر \`<pre>\` در ابتدا دارای ${pre.attributes.length} ویژگی است.\n\n`;

result += "ما `class` را از `<span>` حذف کرده و به `<pre>` اضافه می‌کنیم.\n";
const classAttribute = span.attributes.removeNamedItem("class");
pre.attributes.setNamedItem(classAttribute);
result += `اکنون عنصر \`<pre>\` دارای ${pre.attributes.length} ویژگی است.\n\n`;

result += "ما `id` را از `<span>` می‌گیریم و سعی می‌کنیم آن را به `<pre>` اضافه کنیم.\n";
const id = span.attributes.getNamedItem("id");
try {
  pre.attributes.setNamedItem(id);
} catch (error) {
  result += `یک استثنا رخ داده است: ${error.name}: ${error.message}.\n`;
}

pre.textContent = result;
```

{{EmbedLiveSample("Example", "100%", 160)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}