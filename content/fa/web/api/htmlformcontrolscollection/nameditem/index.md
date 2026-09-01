---
title: "HTMLFormControlsCollection: namedItem() method"
---

---
title: "HTMLFormControlsCollection: namedItem() method"
short-title: namedItem()
slug: Web/API/HTMLFormControlsCollection/namedItem
page-type: web-api-instance-method
browser-compat: api.HTMLFormControlsCollection.namedItem
---

{{APIRef("HTML DOM")}}

متد **`HTMLFormControlsCollection.namedItem()`** یک {{domxref("RadioNodeList")}} یا {{domxref("Element")}} را در مجموعه بازمی‌گرداند که `name` یا `id` آن با نام مشخص‌شده مطابقت داشته باشد؛ اگر هیچ گره‌ای مطابقت نداشته باشد، `null` برمی‌گرداند.

توجه داشته باشید که این نسخه از `namedItem()` نسخهٔ به‌ارث‌برده‌شده از {{domxref("HTMLCollection")}} را پنهان می‌کند. مانند آن نسخه، در جاوااسکریپت، استفاده از نحو براکت آرایه با یک {{jsxref("String")}} مانند `collection["value"]` معادل `collection.namedItem("value")` است.

## Syntax

```js-nolint
namedItem(name)
[name]
```

### Parameters

- `name`
  - : رشته‌ای که برای تطبیق با ویژگی‌های `name` یا `id` کنترلها در این شیء `HTMLFormControlsCollection` استفاده می‌شود.

### Return value

- اگر چندین عنصر دارای `name` یا `id` داده‌شده باشند، یک {{domxref("RadioNodeList")}}؛
- اگر دقیقاً یک عنصر دارای `name` یا `id` داده‌شده باشد، یک {{domxref("Element")}}؛ یا
- اگر هیچ عنصری دارای `name` یا `id` داده‌شده نباشد، [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) برگردانده می‌شود.

> [!NOTE]
> {{domxref("RadioNodeList")}} بازگشتی زنده (live) است؛ یعنی اگر عناصری که با نام داده‌شده مطابقت دارند به مجموعه اضافه یا از آن حذف شوند، محتوای آن به‌طور خودکار به‌روزرسانی می‌شود. علاوه بر این، با وجود نام مجموعه، ممکن است شامل عناصر ورودی غیررادیویی (non-radio) نیز باشد.

## Examples

### Using namedItem()

#### HTML

```html
<form>
  <label for="yes">Yes</label>
  <input id="yes" name="my-radio" type="radio" />
  <label for="no">No</label>
  <input id="no" name="my-radio" type="radio" />
  <label for="maybe">Maybe</label>
  <input id="maybe" name="my-radio" type="radio" />
  <br />
  <label for="text1">Text input 1</label>
  <input id="text1" name="my-form-control" type="text" />
</form>

<div id="output"></div>
```

```css hidden
div {
  margin: 1rem 0;
}
```

#### JavaScript

```js
const form = document.querySelector("form");
const items = form.elements.namedItem("my-radio");

const output = document.querySelector("#output");
const itemIDs = Array.from(items)
  .map((item) => `"${item.id}"`)
  .join(", ");

const item2 = form.elements.namedItem("my-form-control");
output.textContent = `My items: ${itemIDs}
My single item: "${item2.id}"`;
```

#### Result

{{EmbedLiveSample("Using namedItem()")}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLCollection.namedItem")}} که این متد جایگزین آن شده است.